SpringCloud
-----------

### 什么是 Spring Cloud？

1.  Spring Cloud 是一个微服务框架，相比 Dubbo 等 RPC 框架，Spring Cloud 提供的全套的分布式系统解决方案。
2.  Spring Cloud 对微服务基础框架 Netflix 的多个开源组件进行了封装，同时又实现了和云端平台以及和 Spring Boot 开发框架的集成。
3.  Spring Cloud 为微服务架构开发涉及的配置管理，服务治理，熔断机制，智能路由，微代理，控制总线，一次性 token，全局一致性锁，leader 选举，分布式 session，集群状态管理等操作提供了一种简单的开发方式。
4.  Spring Cloud 为开发者提供了快速构建分布式系统的工具，开发者可以快速的启动服务或构建应用、同时能够快速和云平台资源进行对接。

### Spring Cloud 与 Dubbo 的区别是什么？

<table width="1022"><tbody><tr><td colspan="2" width="235">对比项</td><td width="273">Dubbo</td><td width="393">Spring Cloud</td></tr><tr><td colspan="2">出生背景</td><td>阿里系。核心框架是服务化治理</td><td>Spring 社区。核心框架是 Netflix 开源微服务架构群体</td></tr><tr><td rowspan="3">活跃度</td><td>社区活跃度</td><td colspan="2">相差不多但是 Spring Cloud 相对更活跃一些</td></tr><tr><td>百度指数</td><td>2570</td><td>999</td></tr><tr><td>招聘岗位</td><td>636</td><td>160</td></tr><tr><td colspan="2">文档质量</td><td>集中，健全</td><td>较多，内容大部分是英文版</td></tr><tr><td colspan="2">性能</td><td colspan="2">1:3</td></tr><tr><td rowspan="9">功能</td><td>服务注册中心</td><td>ZooKeeper</td><td>Spring Cloud Netflix Eureka</td></tr><tr><td>服务调用方式</td><td>PRC</td><td>REST API</td></tr><tr><td>服务网关</td><td>无</td><td>Spring Cloud Netflix Zuul</td></tr><tr><td>断路由</td><td>集群容错</td><td>Spring Cloud Netflix Hystrix</td></tr><tr><td>分布式配置</td><td>无</td><td>Spring Cloud Config</td></tr><tr><td>服务跟踪</td><td>无</td><td>Spring Cloud Sleuth</td></tr><tr><td>消息总线</td><td>无</td><td>Spring Cloud Bus</td></tr><tr><td>数据流</td><td>无</td><td>Spring Cloud Stream</td></tr><tr><td>批量任务</td><td>无</td><td>Spring Cloud Task</td></tr></tbody></table>

### Spring Cloud 断路器的作用是什么？

在分布式架构中，断路器模式的作用也是类似的，当某个服务单元发生故障（类似用电器发生短路）之后，通过断路器的故障监控（类似熔断保险丝），向调用方返回一个错误响应，而不是长时间的等待。这样就不会使得线程因调用故障服务被长时间占用不释放，避免了故障在分布式系统中的蔓延。

Spring Cloud 的核心组件有哪些？
----------------------

1.  Eureka：服务注册于发现。
2.  Feign：基于动态代理机制，根据注解和选择的机器，拼接请求 url 地址，发起请求。
3.  Ribbon：实现负载均衡，从一个服务的多台机器中选择一台。
4.  Hystrix：提供线程池，不同的服务走不同的线程池，实现了不同服务调用的隔离，避免了服务雪崩的问题。
5.  Zuul：网关管理，由 Zuul 网关转发请求给对应的服务。

### Spring Cloud 如何实现服务的注册？

在服务发布时，需要指定对应的服务名，并将该服务注册到注册中心（例如 Eureka、Zookeeper 等）。可以使用 @EnableEurekaServer 注解开启注册中心，使用 @EnableDiscoveryClient 注解将服务注册到注册中心，然后使用 Ribbon 或 Feign 等工具进行服务之间的调用和发现。这样可以实现服务之间的相互调用，提高应用程序的可扩展性和弹性。

### Eureka 自我保护机制是什么？

当 Eureka Server 节点在短时间内丢失了过多实例的连接时（比如网络故障或频繁启动关闭客户端）节点会进入自我保护模式， 保护注册信息，不再删除注册数据，故障恢复时，自动退出自我保护模式。

### 什么是 Ribbon？

Ribbon 是一个负载均衡客户端，可以很好地控制 HTTP 和 TCP 的一些行为。Feign 默认集成了 Ribbon。

### 什么是 Spring Cloud Bus?

Spring Cloud Bus 将分布式的节点用轻量的消息代理连接起来，它可以用于广播配置文件的更改或者服务直接的通讯，也可用于监控。如果修改了配置文件，发送一次请求，所有的客户端便会重新读取配置文件。

### 什么是 Eureka 注册中心？

Eureka 是 Netflix 开发的服务发现组件，本身是一个基于 REST 的服务。Spring Cloud 将它集成在其子项目 spring-cloud-netflix 中， 以实现 Spring Cloud 的服务注册于发现，同时还提供了负载均衡、故障转移等能力。

### 负载平衡的意义什么？

在计算中，负载平衡可以改善跨计算机，计算机集群，网络链接，中央处理单元或磁盘驱动器等多种计算资源的工作负载分布。负载平衡旨在优化资源使用，最大化吞吐量，最小化响应时间并避免任何单一资源的过载。使用多个组件进行负载平衡而不是单个组件可能会通过冗余来提高可靠性和可用性。负载平衡通常涉及专用软件或硬件，例如多层交换机或域名系统服务器进程。