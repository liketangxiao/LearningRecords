# ORM框架

## Hibernate

### 执行流程

- Configration获取配置文件映射信息
- 获取SessionFactory
- 获取session
- 开启事务，执行操作，关闭事务
- 关闭session sessionFactory

### get和load的区别

- get立即发送sql，load不会立即发送sql 延迟加载
- load不会返回null，因为没有发送sql不知道有没有对应数据
- load通过Hibernate.initialize(obj)创建代理对象，
必须在session关闭前创建

### 持久化对象

- 瞬时状态

	- 刚new出来的对象，不处于session中

- 持久化状态

	- 被持久化，处于session缓存中

- 游离状态

	- 被持久化，不处于session中

- 删除状态

	- 有oid处于session中，计划被删除

- 在提交事物的时候发送sql

### 缓存

- 一级缓存

	- 处于session中，只属于单个request

- 二级缓存

	- 处于sessionFactory中，整个应用都可以使用

### 并发处理

- 悲观锁

	- 查询的时候使用数据库自带的锁

- 乐观锁

	- 添加一个版本号，有冲突就回滚

### spring整合

- 配置数据源，会话工厂，声明式事务
- 事务 配置事务属性，配置事务切点

## Mybatis

### 基本原理

- 数据源 datasource
- 会话工厂 SqlSessionFactory

	- 单例

- 会话 SqlSession

	- 面向用户的接口，线程不安全

- 事务 Transaction
- #{}占位符 ${}拼接符 会引起sql注入

### 动态SQL

- if，sql片段，foreach

### resulMap

- 通过association，collection实现一对一，一对多映射

### 延迟加载

- setting打开延迟加载lazyLodingEnabled，积极加载默认false
- 通过association，collection实现
- 通过定义多个mapper，在程序中实现

### 缓存

- 一级缓存

	- SqlSession级别的缓存，默认开启

- 二级缓存

	- mapper级别的缓存，多个sqlsession可以共用缓存
	- setting打开二级缓存cacheEnabled

- 二级缓存整合ehcache

	- mapper下配置默认缓存为ehcache
	- 加入ehcache.xml配置

### 整合Spring

- 在applicationContext.xml配置datasource,sqlsessionfactory

### statement解析和加载

