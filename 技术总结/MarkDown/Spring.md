# Spring

## Spring AOP

### 切面 Aspect

### 切点 pointCut

### 通知 Advice

### 实现技术

- 编译期间

	-  把切面代码和业务代码编译到一起

- 运行期间 

	- JDK代理方式,需要实现业务接口, 
通过代理类把切面代码放到代理类中

		- Proxy用来创建代理对象，
InvocationHandler用来执行业务逻辑

	- CGlib代理方式, 动态构建业务类的子类,
 将切面代码加入到子类中

### 应用

- 事务
- 安全
- 日志

## Spring IOC

### IOC

- 将代码的控制权交给容器控制

### DI

- 由IOC容器注入对象的依赖组件

	- 工厂模式+反射

### BeanFactory 顶层接口类访问IOC容器的入口

###  创建Bean对象IOC容器

- XmlBeanFactory
- ClassPathXmlApplicationContext
- ApplicationContext

### 管理Bean依赖 

- BeanDefinition将bean.xml转换为Spring能够理解的数据结构

### IOC实现过程

- IOC容器初始化

	- 资源定位

		- XML转换为resource

	- 资源载入

		- resource转换为Bean Definition对象

	- 资源注册

		- 将Bean Definition对象注册到BeanFactory

- 依赖注入

	- 初始化bean
	- 创建bean
	- 注入bean属性

		- 利用反射原理

## Spring 事务

### 编码式事务

- 通过编码的方式实现事务,定义一个切面类

### 声明式事务 基于AOP,
将底层jdbc事务代码嵌入业务代码

- 配置文件
- 注解@Tranceactional

### public和自调用问题

- 配置AspectJ

### Spring Boot事务

- @EnableTranceactionalManagerment
- @Tranceactional

## Bean的生命周期

### 1. 实例化bean，默认bean单例

### 2. bean设置属性值，依赖注入

### 3. 如果实现了BeanNameAware接口,调用setBeanName设置Bean的ID或者Name

### 4. 如果实现BeanFactoryAware接口,调用setBeanFactory 设置BeanFactory

### 5. 如果实现ApplicationContextAware,调用setApplicationContext设置ApplicationContext

### 6. 调用BeanPostProcessor的预先初始化方法

### 7. 调用InitializingBean的afterPropertiesSet()方法

### 8. 调用定制init-method方法

### 9. 调用BeanPostProcessor的后初始化方法

### 1. 调用DisposableBean的destroy()

### 2. 调用定制的destroy-method方法

