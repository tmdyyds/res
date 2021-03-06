## 面试题

#### 大量(批量)key设置同一过期时间？

> 大量key同时过期，在瞬间有大量请求的话，全部打到DB上，造成DB压力过大设置宕机，进而引发服务器崩溃，容易造成缓存雪崩。

- 给每个过期时间设置一个随机值(过期时间+随机值)
- 后台进程定时分批的重新刷新key过期时间，利用expipeat/pexpipeat设置key到何时过期，注意与expipe/pexpipe区别

#### redis如何实现延迟队列？

> 使用sortedset，拿时间戳作为score，消息内容作为key，zadd生产消息，消费者用**zrangebyscore**指令获取N秒之前的数据轮询进行处理

#### Redis是单线程的吗？你确定吗？全部是单线程吗

> Redis 是单线程，主要是指 Redis 的网络 IO 和键值对读写是由一个线程来完成的，这也是 Redis 对外提供键值存储服务的主要流程。但 Redis 的其他功能，比如持久化、异步删除、集群数据同步等，其实是由额外的线程执行的。