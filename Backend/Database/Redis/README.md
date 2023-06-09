Redis 存储系统
==========

## 什么是 Redis？

Remote Dictionary Server (Redis) 是一个开源的使用 ANSI C 语言编写、支持网络、可基于内存亦可持久化的日志型、Key- Value 数据库，并提供多种语言的 API。它通常被称为数据结构服务器，因为值（value）可以是 字符串 (String), 哈希 (Map), 列表 (list), 集合 (sets) 和 有序集合 (sorted sets) 等类型。

## Redis 的特点什么是？

1.  支持多种数据结构，如 String (字符串)、 List (列表)、Hash (哈希表)、Set (集合)、Sorted Set (有序集合)、HyperLogLog (基数估算)。
2.  支持持久化操作，可以进行 aof 及 rdb 数据持久化到磁盘，从而进行数据备份或数据恢复等操作，较好的防止数据丢失的手段。
3.  支持通过 Replication 进行数据复制，通过 master-slave 机制，可以实时进行数据的同步复制，支持多级复制和增量复制，master-slave 机制是 Redis 进行 HA 的重要手段。
4.  单进程请求，所有命令串行执行，并发情况下不需要考虑数据一致性问题。

## Redis 数据类型有哪些？

1.  String (字符串)
2.  Hash (hash 表)
3.  List (链表)
4.  Set (集合)
5.  Sorted Set (有序集合 zset)

## Redis 的配置以及持久化方案有几种？

1.  RDB 方式
2.  AOF 方式

## Redis 中的常用命令哪些？

1.  hset 存储一个哈希键值对的集合
2.  hget 获取一个哈希键的值
3.  hdel 删除一个或多个字段
4.  hgetall 获取一个哈希是键值对的集合
5.  lpush key value 向链表左侧添加
6.  rpush key value 向链表右侧添加
7.  lpop key 从左边移出一个元素
8.  rpop key 从右边移出一个元素
9.  keys \* 返回所有的 key 可以加 \* 通配
10.  exists key 判断 string 类型一个 key 是否存在 如果存在返回 1 否则返回 0

## Redis 主要消耗什么物理资源？

内存

## Redis 有哪几种数据淘汰策略？

1.  noeviction: 返回错误当内存限制达到，并且客户端尝试执行会让更多内存被使用的命令。
2.  allkeys-lru: 尝试回收最少使用的键（LRU），使得新添加的数据有空间存放。
3.  volatile-lru: 尝试回收最少使用的键（LRU），但仅限于在过期集合的键，使得新添加的数据有空间存放。
4.  allkeys-random: 回收随机的键使得新添加的数据有空间存放。
5.  volatile-random: 回收随机的键使得新添加的数据有空间存放，但仅限于在过期集合的键。
6.  volatile-ttl: 回收在过期集合的键，并且优先回收存活时间（TTL）较短的键，使得新添加的数据有空间存放。

## Redis 官方为什么不提供 Windows 版本？

因为目前 Linux 版本已经相当稳定，而且用户量很大，无需开发 windows 版本，反而会带来兼容性等问题。

## 为什么 Redis 需要把所有数据放到内存中？

Redis 为了达到最快的读写速度将数据都读到内存中，并通过异步的方式将数据写入磁盘。所以 Redis 具有快速和数据持久化的特征，如果不将数据放在内存中，磁盘 I/O 速度为严重影响 Redis 的性能。在内存越来越便宜的今天，Redis 将会越来越受欢迎， 如果设置了最大使用的内存，则数据已有记录数达到内存限值后不能继续插入新值。

## Redis 有哪些适合的场景？

1.  会话缓存（Session Cache）：最常用的一种使用 Redis 的情景是会话缓存（Session Cache），用 Redis 缓存会话比其他存储（如 Memcached）的优势在于：Redis 提供持久化。当维护一个不是严格要求一致性的缓存时，如果用户的购物车信息全部丢失，大部分人都会不高兴的，现在，他们还会这样吗？幸运的是，随着 Redis 这些年的改进，很容易找到怎么恰当的使用 Redis 来缓存会话的文档。甚至广为人知的商业平台 Magento 也提供 Redis 的插件。
2.  全页缓存（FPC）：除基本的会话 token 之外，Redis 还提供很简便的 FPC 平台。回到一致性问题，即使重启了 Redis 实例，因为有磁盘的持久化，用户也不会看到页面加载速度的下降，这是一个极大改进，类似 PHP 本地 FPC。再次以 Magento 为例，Magento 提供一个插件来使用 Redis 作为全页缓存后端。此外，对 WordPress 的用户来说，Pantheon 有一个非常好的插件 wp-redis，这个插件能帮助你以最快速度加载你曾浏览过的页面。
3.  队列：Reids 在内存存储引擎领域的一大优点是提供 list 和 set 操作，这使得 Redis 能作为一个很好的消息队列平台来使用。Redis 作为队列使用的操作，就类似于本地程序语言（如 Python）对 list 的 push/pop 操作。如果你快速的在 Google 中搜索 “Redis queues”，你马上就能找到大量的开源项目，这些项目的目的就是利用 Redis 创建非常好的后端工具，以满足各种队列需求。例如，Celery 有一个后台就是使用 Redis 作为 broker，你可以从这里去查看。
4.  排行榜 / 计数器：Redis 在内存中对数字进行递增或递减的操作实现的非常好。集合（Set）和有序集合（SortedSet）也使得我们在执行这些操作的时候变的非常简单，Redis 只是正好提供了这两种数据结构。
5.  发布 / 订阅：最后（但肯定不是最不重要的）是 Redis 的发布 / 订阅功能。发布 / 订阅的使用场景确实非常多。我已看见人们在社交网络连接中使用，还可作为基于发布 / 订阅的脚本触发器，甚至用Redis 的发布/订阅功能来建立聊天系统！