ZooKeeper
---------

### ZooKeeper 是什么？

ZooKeeper 是一个开放源码的分布式协调服务，它是集群的管理者，监视着集群中各个节点的状态根据节点提交的反馈进行下一步合理操作。最终，将简单易用的接口和性能高效、功能稳定的系统提供给用户。分布式应用程序可以基于 Zookeeper 实现诸如数据发布 / 订阅、负载均衡、命名服务、分布式协调 / 通知、集群管理、Master 选举、分布式锁和分布式队列等功能。

### ZooKeeper 提供了什么？

1.  文件系统
2.  通知机制

### Zookeeper 文件系统

Zookeeper 提供一个多层级的节点命名空间（节点称为 znode）。与文件系统不同的是，这些节点都可以设置关联的数据，而文件系统中只有文件节点可以存放数据而目录节点不行。Zookeeper 为了保证高吞吐和低延迟，在内存中维护了这个树状的目录结构，这种特性使得 Zookeeper 不能用于 存放大量的数据，每个节点的存放数据上限为 1M。

### 四种类型的数据节点 Znode

1.  PERSISTENT - 持久化目录节点客户端与 zookeeper 断开连接后，该节点依旧存在。
2.  PERSISTENT\_SEQUENTIAL - 持久化顺序编号目录节点客户端与 zookeeper 断开连接后，该节点依旧存在，只是 Zookeeper 给该节点名称进行序编号。
3.  EPHEMERAL - 临时目录节点客户端与 zookeeper 断开连接后，该节点被删。
4.  EPHEMERAL\_SEQUENTIAL - 临时顺序编号目录节点客户端与 zookeeper 断开连接后，该节点被删除，只是 Zookeeper 给该节点名称进行顺序号。

### Zookeeper 通知机制

Client 端会对某个 ZNode 建立一个 Watcher 事件，当该 ZNode 发生变化时，这些 Client 会收到 ZooKeeper 的通知，然后 Client 可以根据 ZNode 变化来做出业务上的改变等。

### ZooKeeper 负载均衡和 Nginx 负载均衡区别

ZooKeeper 的负载均衡是可以调控，Nginx 只是能调权重，其他需要可控的都需要自己写插件；但是 Nginx 的吞吐量比 ZooKeeper 大很多，应该说按业务选择用哪种方式。

### ZooKeeper 工作原理

ZooKeeper 的核心是原子广播，这个机制保证了各个 Server 之间的同步。实现这个机制的协议叫做 Zab 协议。Zab 协议有两种模式，它们分别是恢复模式（选主）和广播模式（同步）。当服务启动或者在领导者崩溃后，Zab 就进入了恢复模式，当领导者被选举出来，且大多数 Server 完成了和 leader 的状态同步以后，恢复模式就结束了。状态同步保证了 leader 和 Server 具有相同的系统状态。

### ZooKeeper 是如何保证事务的顺序一致性的？

ZooKeeper 采用了递增的事务 ID 来标识，所有的 Proposal（提议）都在被提出的时候加上了 ZXID，ZXID 实际上是一个 64 位的数字，高 32 位是 Epoch（时期；纪元；世；新时代）用来标识 Leader 是否发生改变，如果有新的 Leader 产生出来，Epoch 会自增，低 32 位用来递 增计数。当新产生 Proposal 的时候，会依据数据库的两阶段过程，首先会向其他的 Server 发出事务执行请求，如果超过半数的机器都 能执行并且能够成功，那么就会开始执行。