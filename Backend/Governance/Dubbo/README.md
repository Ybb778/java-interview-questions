Dubbo
-----

### Dubbo 是什么？

Dubbo 是阿里巴巴开源的基于 Java 的高性能 RPC 分布式服务框架，现已成为 Apache 基金会孵化项目。

### Dubbo 默认使用什么注册中心，还有别的选择吗？

推荐使用 ZooKeeper 作为注册中心，还有 Redis、Multicast、Simple 注册中心，但不推荐。

### 在 Provider 上可以配置的 Consumer 端的属性有哪些？

1.  timeout：方法调用超时
2.  retries：失败重试次数，默认重试 2 次
3.  loadbalance：负载均衡算法，默认随机
4.  actives 消费者端，最大并发调用限制

### Dubbo 推荐使用什么序列化框架，你知道的还有哪些？

推荐使用 Hessian 序列化，还有 Duddo、FastJson、Java 自带序列化。

### 你还了解别的分布式框架吗？

别的还有 Spring cloud、Facebook 的 Thrift、Twitter 的 Finagle 等。

### Dubbo 内置了哪几种服务容器？

Spring Container，Jetty Container，Log4j Container

### Dubbo 核心的配置有哪些？

<table width="550"><tbody><tr><td width="155">配置</td><td width="179">配置说明</td></tr><tr><td>dubbo:service</td><td>服务配置</td></tr><tr><td>dubbo:reference</td><td>引用配置</td></tr><tr><td>dubbo:protocol</td><td>协议配置</td></tr><tr><td>dubbo:application</td><td>应用配置</td></tr><tr><td>dubbo:module</td><td>模块配置</td></tr><tr><td>dubbo:registry</td><td>注册中心配置</td></tr><tr><td>dubbo:monitor</td><td>监控中心配置</td></tr><tr><td>dubbo:provider</td><td>提供方配置</td></tr><tr><td>dubbo:consumer</td><td>消费方配置</td></tr><tr><td>dubbo:method</td><td>方法配置</td></tr><tr><td>dubbo:argument</td><td>参数配置</td></tr></tbody></table>

### Dubbo 有哪几种集群容错方案，默认是哪种？

<table width="550"><tbody><tr><td width="161">集群容错方案</td><td width="337">说明</td></tr><tr><td>Failover Cluster</td><td>失败自动切换，自动重试其他服务器（默认）</td></tr><tr><td>Failfast Cluster</td><td>快速失败，立即报错，只发起一次调用</td></tr><tr><td>Failsafe Cluster</td><td>失败安全，出现异常时，直接忽略</td></tr><tr><td>Failback Cluster</td><td>失败自动恢复，记录失败请求，定时重发</td></tr><tr><td>Forking Cluster</td><td>并行调用多个服务器，只要一个成功即返回</td></tr><tr><td>Broadcast Cluster</td><td>广播逐个调用所有提供者，任意一个报错则报错</td></tr></tbody></table>

### Dubbo 有哪几种负载均衡策略，默认是哪种？

<table width="627"><tbody><tr><td width="199">负载均衡策略</td><td width="307">说明</td></tr><tr><td>Random LoadBalance</td><td>随机，按权重设置随机概率（默认）</td></tr><tr><td>RoundRobin LoadBalance</td><td>轮询，按公约后的权重设置轮询比率</td></tr><tr><td>LeastActive LoadBalance</td><td>最少活跃调用数，相同活跃数的随机</td></tr><tr><td>ConsistentHash LoadBalance</td><td>一致性 Hash，相同参数的请求总是发到同一提供者</td></tr></tbody></table>

### Dubbo 的优势

1.  单一应用架构，当网站流量很小时，只需一个应用，将所有功能都部署在一起，以减少部署节点和成本。此时，用于简化增 删改查工作量的 数据访问框架（ORM）是关键。
2.  垂直应用架构，当访问量逐渐增大，单一应用增加机器带来的加速度越来越小，将应用拆成互不相干的几个应用，以提升效 率。此时，用于加速前端页面开发的 Web 框架（MVC）是关键。
3.  分布式服务架构，当垂直应用越来越多，应用之间交互不可避免，将核心业务抽取出来，作为独立的服务，逐渐形成稳定的 服务中心，使前端应用能更快速的响应多变的市场需求。此时，用于提高业务复用及整合的 分布式服务框架（RPC）是关键。
4.  流动计算架构当服务越来越多，容量的评估，小服务资源的浪费等问题逐渐显现，此时需增加一个调度中心基于访问压力实时管理集群容量，提高集群利用率。此时，用于提高机器利用率的 资源调度和治理中心（SOA）是关键。