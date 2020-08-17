# SpringBoot-RabbitMQ实现延迟队列

## 两个特性

- time-to-live Extentions TTL 消息存活时间
- Dead-letter Exchanges DLX 消息过期 ' 死亡 ' 转发

## 流程图

```flow
st=>start: 生产者
e=>end: 消费者
op1=>operation: 缓冲队列
op2=>operation: 实际消费队列
op3=>operation: DLX
st(right)->op1(right)->op3
op3(right)->op2(right)->e
```

