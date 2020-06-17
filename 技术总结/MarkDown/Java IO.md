# Java IO

## 磁盘操作 File

## 字节操作 In/OutPutStream

### 使用装饰者模式实现

### 使用缓存就在FileInputStream套上一层BuffedInputStream

## 字符操作 Read/Writer

## 对象操作 Serializable

### 序列化 ObjectOutputStream.writerObject()

### 反序列化 ObjectInputStream.readObject();

### 不会对静态变量序列化, 只序列化对象的状态

### ArrayList存储数组用transient修饰, 只序列化有数据的部分

## 网络操作 Socket

### InetAddress 获取IP

### URL 

### Sockets 使用TCP协议

### DataGram 使用UDP协议

## NIO

### 流与块

- NIO处理数据块，速度快
- NIO 实现了 IO 多路复用中的 Reactor 模型

### 选择器 Selector

- 基于 事件驱动，监听多个通道的channel的事件，
达到一个线程处理多个事件
- 非阻塞 当channel上的IO还未到达时不会阻塞，会执行其他channel
- 轮询已注册的 Channel.register(selector, SelectionKey.OP_ACCEPT)
- 监听事件 selector.select()
- 只有套接字channel才能配置非阻塞，fileChannel不能配置非阻塞

### 通道 Channel

- 双向读取或写入数据 buffer.flip();
- FileChannel 从文件中读取数据
- DatagramChannel 从UDP读写网络中的数据
- SocketChannel 通过TCP读写网络中的数据
- ServerSoketChannel 监听网络中TCP连接，
为每个连接创建SocketChannel

### 缓冲区 Buffer

- 缓冲区用来接收通道的数据
- 实质上是一个数组，提供对数据的结构化访问
- capacity

	- 缓冲区的容量

- limit

	- 缓冲区还可以读写的字节数

-  position

	- 当前已经读写的字节数

## Netty

### 基于NIO的开源框架

### Reactor模型

- 多路复用器Acceptor
- 事件分发器Dispatches
- 事件处理器Handler
- 单线程模式

	- 所有I/O操作都在Reactor上执行

- 多线程模式

	- 多路复用线程监听服务端的请求
	- 线程池处理NIO的读写操作

- 主从多线程模式

	- 多个Reactor线程，主线程建立链路之后，注册到从线程处理NIO读写

### 服务端

- NioEventLoopGroup

	- boss

		- 处理客户端请求

	- worker

		- 处理客户端数据读写操作

- ServerBootstrap

	- 启动辅助类，用来注册Socket参数
	- .group().channal().option().handler()

- 绑定端口

### 客户端

- EventLoopGroup
- Bootstrap

