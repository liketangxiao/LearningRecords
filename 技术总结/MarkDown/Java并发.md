# Java 并发

## 线程状态转换

### 新建

### 可运行

### 等待 主动调用sleep();Wait()

### 阻塞 被动等待锁

### 死亡

## 使用线程

### 继承Thread

### 实现Runnable

### 实现Callable

## 线程机制

### 线程池 Executor

- ThreadPoolExecutor工厂方法
- NewFixedThreadPool,NewSingletonThreadPool
- NewCachedThreadPool,NewSechduledThreadPool
- 拒绝策略：高峰期拒绝记录日志，在不是高峰期再处理日志

### 守护线程 deamon

### sleep();

### yield();

## 中断

### interrupt()和interrupted();

- 不能中断I/O阻塞, synchronized锁阻塞
- 等待或者阻塞调用会抛出InterruptedException异常

### Executor.shutdown();

### Executor.submit()返回Future对象,调用cancel();

## 互斥同步

### Synchronize

- JVM实现 synchronized JVM通过进入，退出对象监视器
来实现对方法，同步块同步的
- 做了许多优化,优先选择synchronized

### RetrantLock

- JDK实现 可实现等待中断, 公平锁, 绑定多个条件
- 重入锁

	- ReentrantLock判断当前线程是否为获取锁的线程,
是则同步状态+1,否则-1，同步状态为0时释放锁

- 读写锁

	- ReentrantReadWriteLock写线程会阻塞，读线程不会阻塞

## 线程协作

### join();

- 将当前线程挂起, 直至目标线程结束

### wait();notify();

- 将等待的线程挂起, 唤醒

### await();signal();

- concurrent包下的Condition类提供

## J.U.C-AQS

### AbstractQueuedSynchronizer

- AQS是JUC的核心

### CountDownLatch.await()

- 控制线程等待多个线程

### CyclicBarrier.await()

- 控制线程等待,可循环

### semaphore.acquire()

- 控制互斥资源的线程访问数

### futureTask

- 获取线程执行结果或取消执行
- 实现Callable接口返回值, 或者Executor.submit()返回值

### BlockingQueue

- 实现阻塞队列
- LinkedBlockingQueue,ArrayBlockingQueue, PriorityBlockingQueue

## Java内存模型

### Thread 执行获取结果

### 工作内存 保存变量副本

### 主内存 保存变量和变量值传递

### 原子性

- 要么执行, 要么不执行,操作不可中断
- AtomicInteger, synchronize保证原子性

###  可见性 

- 一个线程对共享变量的修改可被其他线程知道
- volatile, synchronize, final可保证可见性

###  有序性

- 线程内的操作都是有序的, 不会发生指令重排
- volatile, synchronize, 可保证有序性

## 线程安全性

### 不可变 绝对安全 相对安全

## 线程安全实现方法

### 阻塞同步

- 悲观并发策略synchronize和reentrantLock

### 非阻塞同步

- 乐观并发策略 先操作和冲突检测, 补偿方法一般为重试
- atomicInteger 使用了Unsafe类的CAS操作
- CAS存在ABA问题, 可以使用版本来进行检测
- CAS来保证操作和冲突检测的原子性

### 无同步方案

- 可重入代码ReentrantCode 如递归可中断执行代码而且去执行另一段代码, 控制权返回后原来的程序不会出现错误
- 栈封闭 只使用局部变量,属于线程私有
- 线程本地存储ThreadLocal 保证共享数据在同一线程中执行

## 锁优化

### 自旋锁 线程在获取锁的期间执行自循环直至获取锁

### 锁消除 主内存的数据不可能被其他线程访问到, String的+操作会处理成StringBuild的append()操作

### 锁粗化 一系列操作都对同一个对象加锁和解锁

### 无锁

### 偏向锁 第一个获取锁的线程之后不需要获取该锁

### 轻量级锁 CAS进行同步, 失败转互斥锁

### 重量级锁 互斥锁

## 实践

### 给线程一个有意义的名字, 方便找bug

### 缩小同步的范围

### 多用同步类CountDownLatch, CyclicBarrier, Semaphore, 少用wait()notify();

### 多用并发集合少用同步集合, 使用ConcurrentHashMap而不是HashTable

### 使用本地变量和不可变类保证线程安全

### 使用线程池而不是创建Thread对象

### 使用BlockingQueue实现生产者消费者问题

