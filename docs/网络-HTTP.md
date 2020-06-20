# HTTP

## 基本概念

### http方法

get post put delete patch options connect trace head

### http状态码

### http首部

## 具体应用

### cookie

- 保存状态信息 会话状态, 个性化设置, 浏览器跟踪
- set-cookie保存到浏览器
- secure HTTPS使用 httpOnly只读cookie

### session

- 存储在服务器端 redis
- 返回set-cookie sessionId
- 禁用cookie 使用浏览器重写将sessionID作为参数传递

### 缓存

- cache-control
- 浏览器缓存 代理服务器缓存

### 连接管理

- 长连接/短连接 connection

### 通信数据转发

- 代理 缓存,负载均衡,网络控制访问,访问日志
- 网关 将http转换为其他协议访问非http服务器
- 隧道 使用SSL加密手段实现安全通信

## https

### http先和SSL通信, SSL再和TCP通信 使用了隧道进行通信

### 加密 防窃听

- 对称加密 加密解密使用同一密钥
- 非对称加密

	- 加密解密使用不同密钥
	- 发送方获取公玥加密, 接收方使用私玥解密
	- 可以用来加密，签名

- https采用混合加密机制 使用非对称密钥加密对称密钥保证安全,
 对称密钥加密通信内容保证效率

### 认证 防伪装

- 使用证书对通信双方进行认证

### 完整性保护 防篡改

- 加密和认证保证了完整性

## WEB攻击技术

### 跨站脚本攻击 XSS 获取用户信息执行脚本

- cookie设为httponly
- 过滤特殊字符 < &lt;

### 跨站请求攻击 CSRF 在认证过的网站执行一些操作

- 检查referer字段是否是同一域名下
- 增加token校验

### SQL注入攻击 SQL拼接完成注入

- 使用参数查询

### 拒绝服务攻击 DoS 耗尽目标服务器的网络或系统资源

## GET和POST

### 作用 get用于获取资源 post用于更新资源

### 参数 get在url中, post在请求体zhong

### 安全 get不会改变服务器状态

### 可缓存 get属于可缓存的方法 

### 幂等性 get请求多次结果不变

