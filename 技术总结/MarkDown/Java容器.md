# Java 容器

## Collection

## Map

### HashMap

- 基于哈希实现

### LinkedHashMap

- 使用链表维护元素的顺序

### TreeMap

- 基于红黑树实现

## 设计模式

### 迭代器模式

- Collection实现了Iterable接口

### 适配器模式

- Arrays.asList(T..t)

## ArrayList

### 基于动态数组 实现RandomAccess支持随机访问

### 序列化 Transient只序列化有数据部分 
重写writerObject(),readObject()方法

### 扩容 grow()

### 删除 调用System.arrayCopy()

### fail-fast 比较序列化前后modCount的变化

### Vector ArrayList的同步版本Collections.synchronizedList()

## LinkedList

### 基于双向链表

### 插入时只移动指针，效率比拷贝数组高

### 查找是遍历获取，效率低

## HashMap

### 存储结构 Entry类型的table数组

### 查找分两步,计算键值所在的桶, 在链表上顺序查找

### 使用链表头插法, 将键值插在链表的头部

### 扩容重新计算Hash值,把旧的Table插入到新的Table 

### 死循环

- 并发环境下，扩容rehash时容易出现环形链表

## ConcurrentHashMap

### 分段锁Segment,每个锁维护这几个桶HashEntry,可以多个线程访问不同分段锁上的桶

### 分段锁继承ReentrantLock, count统计Segment上键值的个数

### get方法不需要加锁，hashEntry的value是volatile修饰保证内存可见性

### put方法需要加锁，通过key定位到Segment

### size方法不加锁，count累加统计数量两次，不一样再加锁统计

