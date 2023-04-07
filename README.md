# Java面试宝典

![](https://snowice.fun/wp-content/uploads/2023/03/R-C-1-1.jpg)

### JDK,JRE,JVM 三者关系？

1.  JDK 是 JAVA 程序开发时用的开发工具包，其内部也有 JRE 运行环境 JRE。
2.  JRE 是 JAVA 程序运行时需要的运行环境，就是说如果你光是运行 JAVA 程序而不是去搞开发的话，只安装 JRE 就能运行已经存在的 JAVA 程序了。
3.  JDk、JRE 内部都包含 JAVA 虚拟机 JVM，JAVA 虚拟机内部包含许多应用程序的类的解释器和类加载器等等。

### 面向过程和面向对象的区别？

1.  两者都是软件开发思想，先有面向过程，后有面向对象。在大型项目中，针对面向过程的不足推出了面向对象开发思想。
2.  编程思路不同：面向过程以实现功能的函数开发为主，而面向对象要首先抽象出类、属性及其方法，然后通过实例化类、执行方法来完成功能。
3.  封装性：都具有封装性，但是面向过程是封装的是功能，而面向对象封装的是数据和功能。面向对象具有继承性和多态性， 而面向过程没有继承性和多态 性，所以面向对象优势是明显。

### Java 有哪些基本数据类型？

定义：Java 语言是强类型语言，对于每一种数据都定义了明确的具体的数据类型，在内存中分配了不同大小的内存空间。

*   数值型：整数类型 (byte,short,int,long)
*   数值型：浮点类型 (float,double)
*   字符型 (char)
*   布尔型 (boolean)

### 什么 Java 注释？

1.  定义：用于解释说明程序的
2.  文字分类：
    *   单行注释：格式： // 注释文字多
    *   行注释：格式： /\* 注释文字 \*/
    *   文档注释：格式：/\*\* 注释文字 \*/
3.  作用：在程序中，尤其是复杂的程序中，适当地加入注释可以增加程序的可读性，有利于程序的修改、调试和交流。注释的内容在程序编译的时候会被忽视，不会产生目标代码，注释的部分不会对程序的执行结果产生任何影响。

注意事项：多行和文档注释都不能嵌套使用。

### 数组和集合有什么区别？

1.  数组的长度是固定的，集合的长度是可变的。
2.  数组中存储的是一种类型的元素，可以存储任意类型数据。
3.  集合存储的都是引用数据类型，如果想存储基本类型数据需要存储对应的包装类型。

### final 有什么用？

用于修饰类、属性和方法；

1.  被 final 修饰的类不可以被继承
2.  被 final 修饰的方法不可以被重写
3.  被 final 修饰的变量不可以被改变，被 final 修饰不可变的是变量的引用，而不是引用指向的内容，引用指向的内容是可以改变的

### final fially finalize 区别

1.  final 可以修饰类、变量、方法，修饰类表示该类不能被继承、修饰方法表示该方法不能被重写、修饰变量表示该变量是一个常量不能被重新赋值。
2.  finally 一般作用在 try-catch 代码块中，在处理异常的时候，通常我们将一定要执行的代码方法放在 finally 代码块中，表示不管是否出现异常，该代码块都会执行，一般用来存放一些关闭资源的代码。
3.  finalize 是一个方法，属于 Object 类的一个方法，而 Object 类是所有类的父类，该方法一般由垃圾回收器来调用，当我们调用 System.gc () 方法的时候，由垃圾回收器调用 finalize ()，回收垃圾，一个对象是否可回收的最后判断。

### 面向对象三大特性

1.  封装：隐藏对象的属性和实现细节，仅对外提供公共访问方式，将变化隔离，便于使用，提高复用性和安全性。
2.  继承：继承是使用已存在的类的定义作为基础建立新类的技术，新类的定义可以增加新的数据或新的功能，也可以用父类的功能，但不能选择性地继承父类。通过使用继承可以提高代码复用性。继承是多态的前提。
3.  所谓多态就是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量到底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在由程序运行期间才能决定。

### == 和 equals 的区别是什么？

1.  == : 它的作用是判断两个对象的地址是不是相等。即判断两个对象是不是同一个对象。(基本数据类型 == 比较的是值，引用数据类型 == 比较的是内存地址)
2.  equals () : 它的作用也是判断两个对象是否相等。但它一般有两种使用情况：
    *   情况 1：类没有覆盖 equals () 方法。则通过 equals () 比较该类的两个对象时，等价于通过 “==” 比较这两个对象。
    *   情况 2：类覆盖了 equals () 方法。一般，我们都覆盖 equals () 方法来两个对象的内容相等；若它们的内容相等，则返回 true (即，认为这两个对象相等)。

### String 类的常用方法都有那些？

1.  indexOf ()：返回指定字符的索引。
2.  charAt ()：返回指定索引处的字符。
3.  replace ()：字符串替换。
4.  trim ()：去除字符串两端空白。
5.  split ()：分割字符串，返回一个分割后的字符串数组。
6.  getBytes ()：返回字符串的 byte 类型数组。
7.  length ()：返回字符串长度。
8.  toLowerCase ()：将字符串转成小写字母。
9.  toUpperCase ()：将字符串转成大写字符。
10.  substring ()：截取字符串。
11.  equals ()：字符串比较。

### String 和 StringBuffer、StringBuilder 的区别是什么？String 为什么是不可变的？

StringBuffer 仅能获得 10%~15% 左右的性能提升，但却要冒多线程不安全的风险。

对于三者使用的总结：如果要操作少量的数据用 = String，单线程操作字符串缓冲区 下操作大量数据 = StringBuilder，多线程操作字符串缓冲区 下操作大量数据 = StringBuffer

ChatGPT 的回答：

![](https://image.snowice.fun/blog-image/java/javamsbd/java%E9%9D%A2%E8%AF%95%E5%AE%9D%E5%85%B801.png)

### 自动装箱与拆箱

1.  装箱：将基本类型用它们对应的引用类型包装起来；
2.  拆箱：将包装类型转换为基本数据类型；

### int 和 Integer 有什么区别？

Java 是一个近乎纯洁的面向对象编程语言，但是为了编程的方便还是引入了基本数据类型，但是为了能够将这些基本数据类型当成对象操作，Java 为每一个基本数据类型都引入了对应的包装类型（wrapper class），int 的包装类就是 Integer，从 Java 5 开始引入了自动装箱 / 拆箱机制，使得二者可以相互转换。

### Java 为每个原始类型提供了哪些包装类型？

*   原始类型: boolean，char，byte，short，int，long，float，double
*   包装类型：Boolean，Character，Byte，Short，Integer，Long，Float，Double

### ArrayList、LinkedList、Vector 的区别？

1.  ArrayList,Vector 底层是由数组实现，LinkedList 底层是由双线链表实现，从底层的实现可以得出它们的性能问题。
2.  ArrayList,Vector 插入速度相对较慢，查询速度相对较快，而 LinkedList 插入速度较快，而查询速度较慢。再者由于 Vevtor 使用了线程安全锁，所以 ArrayList 的运行效率高于 Vector。

### HashMap 和 Hashtable 的区别？

1.  线程是否安全： HashMap 是非线程安全的，HashTable 是线程安全的；HashTable 内部的方法基本都经过 synchronized 修饰。（如果你要保证线程安全的话就使用 ConcurrentHashMap 吧！）；
2.  效率： 因为线程安全的问题，HashMap 要比 HashTable 效率高一点。另外，HashTable 基本被淘汰，不要在代码中使用它；
3.  对 Null key 和 Null value 的支持： HashMap 中，null 可以作为键，这样的键只有一个，可以有一个或多个键所对应的值为 null。但是在 HashTable 中 put 进的键值只要有一个
4.  初始容量大小和每次扩充容量大小的不同 ： ①创建时如果不指定容量初始值，Hashtable 默认的初始大小为 11，之后每次扩充，容量变为原来的 2n+1。HashMap 默认的初始化大小为 16。之后每次扩充，容量变为原来的 2 倍。②创建时如果给定了 容量初始值，那么 Hashtable 会直接使用你给定的大小，而 HashMap 会将其扩充为 2 的幂次方大小。也就是说 HashMap 总是使用 2 的幂作为哈希表的大小
5.  底层数据结构： JDK1.8 以后的 HashMap 在解决哈希冲突时有了较大的变化，当链表长度大于阈值（默认为 8）时，将链  
    表转化为红黑树，以减少搜索时间。Hashtable 没有这样的机制。

### Synchronized 用过吗，其原理是什么？

1.  Synchronized 是由 JVM 实现的一种实现互斥同步的一种方式，如果你查看被 Synchronized 修饰过的程序块编译后的字节码，会发现被 Synchronized 修饰过的程 序块，在编译前后被编译器生成了 monitorenter 和 monitorexit 两个字节码指令。
2.  这两个指令是什么意思呢？当虚拟机执行到 monitorenter 指令时，首先要尝试获取对象的锁：如果这个对象没有被其他线程锁定，或者当前线程已经拥有了这个对象的锁，那么就将锁的计数器加 1。当执行 monitorexit 指令时，需要释放对象的锁，将锁计数器减 1。
3.  如果获取对象的锁失败，当前线程就会被阻塞等待，直到对象的锁被另外一个线程释放为止。在 Java 中，使用 synchronized 关键字来实现同步操作，它通过在对象头部设置标记来达到获取锁和释放锁的目的。

### 为什么说 Synchronized 是非公平锁？

非公平锁的主要表现在获取锁的行为上，它并不按照申请锁的时间前后给等待线程分配锁，而是每当锁被释放后，任何一个线程都有机会竞争到锁。这样做的目的是为了提高执行性能，但缺点是可能会产生线程饥饿现象。

### 为什么说 Synchronized 是一个悲观锁？乐观锁的实现原理又是什么？什么是 CAS，它有什么特性？

1.  Synchronized 显然是一个悲观锁，因为它的并发策略是悲观的：不管是否会产生竞争，任何的数据操作都必须要加锁、用户态和核心态转换、维护锁计数器和检查是否有被阻塞的线程需要被唤醒等操作。
2.  随着硬件指令集的发展，我们可以使用基于冲突检测的乐观并发策略。先进行操作，如果没有其他线程征用数据，那操作就成功了；如果共享数据被征用，产生了冲突，那就再进行其他的补偿措施。这种乐观的并发策略的许多实现不需要线程挂起，所以被称为非阻塞同步。
3.  乐观锁的核心算法是 CAS（Compare and Swap，比较并交换），它涉及到三个操作数：内存值、期望值、新值。当且仅当期望值和内存值相等时才将内存值修改为新值。这样处理的逻辑是，首先检查某块内存的值是否跟之前我读取时的一样。如果不一样，则表示期间此内存值已经被其他线程更改过，舍弃本次操作；否则说明期间没有其他线程对此内存值操作，可以把新值设置给此块内存。
4.  CAS 具有原子性，它的原子性由 CPU 硬件指令实现保证，即使用 JNI 调用 Native 方法调用由 C++ 编写的硬件级别指令，JDK 中提供了 Unsafe 类执行这些操作

### 乐观锁一定就是好的吗？

乐观锁避免了悲观锁独占对象的现象，同时也提高了并发性能，但它也有缺点：

1.  乐观锁只能保证一个共享变量的原子操作。如果多一个或几个变量，乐观锁将变得力不从心，但互斥锁能轻易解决，不管对象数量多少及对象颗粒度大小。
2.  长时间自旋可能导致开销大。假如 CAS 长时间不成功而一直自旋，会给 CPU 带来很大的开销。
3.  ABA 问题。CAS 的核心思想是通过比对内存值与预期值是否一样而判断内存值是否被改过，但这个判断逻辑不严谨。假如内存值原来是 A，后来被一条线程改为 B，最后又被改成了 A，则 CAS 认为此内存值并没有发生改变，但实际上是有被其他线程改过的。这种情况对依赖过程值的场景的运算结果影响很大。解决的思路是引入版本号，每次变量更新都把版本号加一。

JDBC 技术
-------

### 什么是 JDBC，在什么时候会用到它？

JDBC 的全称是 Java Database Connection，也就是 Java 数据库连接，我们可以用它来操作关系型数据库。JDBC 接口及相关类在 java.sql 包和 javax.sql 包里。我们可以用它来连接数据库，执行 SQL 查询，存储过程，并处理返回的结果。JDBC 接口让 Java 程序和 JDBC 驱动实现了松耦合，使得切换不同的数据库变得更加简单。

### JDBC 访问数据库的基本步骤是什么？

1.  加载（注册）数据库驱动（到 JVM）
2.  建立（获取）数据库连接。
3.  创建（获取）数据库操作对象。
4.  定义操作的 SQL 语句。
5.  执行数据库操作。
6.  获取并操作结果集。
7.  关闭对象，回收数据库资源（关闭结果集–> 关闭数据库操作对象–> 关闭连接）

### execute, executeQuery, executeUpdate 的区别是什么？

1.  Statement 的 execute (String query) 方法用于执行任意的 SQL 查询。如果查询的结果是一个 ResultSet，则该方法返回 true。如果结果不是 ResultSet，例如 insert 或者 update 查询，则该方法返回 false。
2.  Statement 的 executeQuery (String query) 接口用来执行 select 查询，并且返回 ResultSet。即使查询不到记录返回的 ResultSet 也不会为 null。我们通常使用 executeQuery 来执行查询语句，这样的话如果传进来的是 insert 或者 update 语句的话，它会抛出错误信息为 “executeQuery method can not be used for update” 的 java.util.SQLException。
3.  Statement 的 executeUpdate (String query) 方法用于执行 insert、update 或 delete（DML）语句。
4.  只有当你不确定是什么语句的时候才应该使用 execute () 方法，否则应该使用 executeQuery 或者 executeUpdate 方法。

### JDBC 的 PreparedStatement 是什么？

PreparedStatement 对象代表的是一个预编译的 SQL 语句。通过它提供的 setter 方法，可以传入查询的变量。由于 PreparedStatement 是预编译的，可以高效地多次执行对应的 SQL 语句。PreparedStatement 还自动对特殊字符进行转义，避免了 SQL 注入攻击，因此应该尽可能地使用它。

### 相对于 Statement，PreparedStatement 的优点是什么？

1.  PreparedStatement 有助于防止 SQL 注入，因为它会自动对特殊字符转义。
2.  PreparedStatement 可以用来进行动态查询。
3.  PreparedStatement 执行更快。尤其当你重用它或者使用它的拼量查询接口执行多条语句时。
4.  使用 PreparedStatement 的 setter 方法更容易编写面向对象的代码，而使用 Statement 则需要拼接字符串来生成查询语句。如果参数过多，字符串拼接看起来会很丑陋，而且容易出错。

### JDBC 的 ResultSet 是什么？

在查询数据库后，会返回一个 ResultSet 对象，它就像是查询结果集的一张数据表。ResultSet 对象维护了一个游标，指向当前的数据行。开始时，游标指向第一行。如果调用 ResultSet 的 next () 方法，游标会下移一行，如果没有更多的数据，next () 方法会返回 false。可以在 for 循环中使用它来遍历数据集。

### java.util.Date 和 java.sql.Date 有什么区别？

java.util.Date 包含日期和时间信息，而 java.sql.Date 只包含日期信息，没有具体的时间信息。如果你想在数据库中存储时间信息，可以考虑使用 Timestamp 或者 DateTime 字段。

### 说说事务的概念，在 JDBC 编程中处理事务的步骤？

事务是作为单个逻辑工作单元执行的一系列操作。一个逻辑工作单元必须有四个属性，称为原子性、一致性、隔离性和持久性 (ACID) 属性，只有这样才能成为一个事务。JDBC 处理事务有如下操作：

*   conn.setAutoCommit (false); 设置提交方式为手动提交。
*   conn.commit (); 提交事务。
*   conn.rollback (); 回滚操作。

提交与回滚只选择一个执行。正常情况下，提交事务。如果出现异常，则回滚。

### 数据库连接池的原理。为什么要使用连接池？

1.  数据库连接是一种关键的、有限的、昂贵的资源。对数据库连接的管理能显著影响整个应用程序的伸缩性和健壮性，进而影响程序的性能指标。数据库连接池正是为解决这个问题而提出的。
2.  数据库连接池负责分配、管理和释放数据库连接。它允许应用程序重复使用一个现有的数据库连接，而不是重新建立一个。同时，它也会释放空闲时间超过最大空闲时间的数据库连接，以避免因为没有释放数据库连接而引起的数据库连接遗漏。这项技术可以明显提高对数据库操作的性能。
3.  数据库连接池在初始化时将创建一定数量的数据库连接放到连接池中，这些数据库连接的数量是由最小数据库连接数来设定的。无论这些数据库连接是否被使用，连接池都将一直保证至少拥有这么多的连接数量。连接池的最大数据库连接数量限定了这个连接池能占有的最大连接数。当应用程序向连接池请求的连接数超过最大连接数量时，这些请求将被加入到等待队列中。

### 什么是 JDBC 的最佳实践？

1.  数据库资源是非常昂贵的，用完了应该尽快关闭它。Connection、Statement、ResultSet 等 JDBC 对象都有 close 方法，调用它就好了。
2.  养成在代码中显式关闭掉 ResultSet、Statement、Connection 的习惯。如果你用的是连接池的话，连接用完后会放回池里，但是没有关闭的 ResultSet 和 Statement 就会造成资源泄漏。
3.  在 finally 块中关闭资源，保证即便出了异常也能正常关闭。
4.  尽量使用 PreparedStatement 而不是 Statement，以避免 SQL 注入，同时还能通过预编译和缓存机制提升执行的效率。
5.  数据库隔离级别越高性能越差，确保你的数据库连接设置的隔离级别是最优的。
6.  如果在 WEB 程序中创建数据库连接，最好通过 JNDI 使用 JDBC 的数据源，这样可以对连接进行重用。

Mysql 数据库技术
-----------

### 数据库 MySQL 分页时用的语句

使用 `limit` 关键字。`Select * from 表名 where 条件 limit 开始位置,结束位置`。通过动态的改变开始和结束位置的值来实现分页。

### 根据你以往的经验简单叙述一下 MySQL 的优化

1.  尽可能使用更小的整数类型（`mediumint` 就比 `int` 更合适）
2.  如果想要清空表的所有记录，建议用 `truncate table tablename` 而不是 `delete from tablename`
3.  尽可能的定义字段为 `not null`，除非这个字段需要 `null`。
4.  避免出现 `SELECT * FROM table` 语句，要明确查出的字段。
5.  小心使用 `IN` 和 `OR`，需要注意 `IN` 集合中的数据量。建议集合中的数据不超过 200 个。

### 有两张表；请用 SQL 查询，所有的客户订单日期最新的前五条订单记录。

客户信息表 (c\_CUSTOM) 有以下字段：id、name、mobile

客户订单表 (C\_ORDER) 有以下字段: id, custom\_id, commodity, count, order\_date.

```
	SELECT * FROM c_order ORDER BY order_date DESC LIMIT 0,5;
```

### 数据库设计中，一对多如何处理？

数据库外键关系表示的其实是一种一对多关系，所以处理一对多时可以使用外键。

### 数据库设计中，多对多一般如何处理？

引入中间表，把一个多对多表示为两个一对多。

### MySQL 数据库中，常用的数据类型

<table width="619"><tbody><tr><td width="132">类型名称</td><td width="423">说明</td></tr><tr><td>int(Integer)</td><td>整数类型</td></tr><tr><td>double</td><td>小数类型</td></tr><tr><td>decimal(m,d)</td><td>指定整数位与小数位长度的小数类型</td></tr><tr><td>date</td><td>日期类型，格式为 yyyy-MM-dd，包含年月日，不包含时分秒</td></tr><tr><td>datetime</td><td>日期类型，格式为 yyyy-MM-dd HH:mm:ss，包含年月日时分秒</td></tr><tr><td>timestamp</td><td>日期类型，时间戳</td></tr><tr><td>varchar(M)</td><td>文本类型，M 为 0~65535 之间的整数</td></tr></tbody></table>

### Student 学生表（学号，姓名、性别、年龄、组织部门），Course 课程表（编号，课程名称），Sc 选课表（学号，课程编号，成绩）

*   写一个 SQL 语句，查询选修了计算机原理的学生学号和姓名

```
	select 学号，姓名 from Student where 学号 in（select 学号 from Sc where 课程编号 in(Select 课程编号 from Course where 课程名称 = ‘计算机原理’)）
```

*   写一个 SQL 语句，查询 “周星驰” 同学选修了的课程名字

```
	select 课程名称 from Course where 编号 in (select Sc.课程编号 from Student,Sc where Student.姓名=’周星驰’ and Student.学号 = Sc.学号)
```

### 表结构说明

下面是学生表的（Student）的结构说明

<table border="0" width="345" cellspacing="0" cellpadding="0"><tbody><tr><td width="69" height="19">字段名称</td><td width="69">字段解释</td><td width="69">字段类型</td><td width="69">字段长度</td><td width="69">约束</td></tr><tr><td height="19">s_id</td><td>学号</td><td>字符</td><td>10</td><td>PK</td></tr><tr><td height="19">s_name</td><td>学生姓名</td><td>字符</td><td>50</td><td>Not Null</td></tr><tr><td height="19">s_age</td><td>学生年龄</td><td>数值</td><td>3</td><td>Not Null</td></tr><tr><td height="19">s_sex</td><td>学生性别</td><td>字符</td><td>1</td><td>Not Null</td></tr></tbody></table>

下面是教师表（Teacher ）的结构说明

<table border="0" width="345" cellspacing="0" cellpadding="0"><tbody><tr><td width="69" height="19">字段名称</td><td width="69">字段解释</td><td width="69">字段类型</td><td width="69">字段长度</td><td width="69">约束</td></tr><tr><td height="19">t_id</td><td>教师编号</td><td>字符</td><td>10</td><td>PK</td></tr><tr><td height="19">t_name</td><td>教师姓名</td><td>字符</td><td>50</td><td>Not Null</td></tr></tbody></table>

下面是课程表（Course）的结构说明

<table border="0" width="345" cellspacing="0" cellpadding="0"><tbody><tr><td width="69" height="19">字段名称</td><td width="69">字段解释</td><td width="69">字段类型</td><td width="69">字段长度</td><td width="69">约束</td></tr><tr><td height="19">c_id</td><td>课程编号</td><td>字符</td><td>10</td><td>PK</td></tr><tr><td height="19">c_name</td><td>课程名字</td><td>字符</td><td>50</td><td>Not Null</td></tr><tr><td height="19">t_id</td><td>教师编号</td><td>字符</td><td>10</td><td>Not Null</td></tr></tbody></table>

下面是成绩表（SC）的结构说明

<table border="0" width="345" cellspacing="0" cellpadding="0"><tbody><tr><td width="69" height="19">字段名称</td><td width="69">字段解释</td><td width="69">字段类型</td><td width="69">字段长度</td><td width="69">约束</td></tr><tr><td height="19">s_id</td><td>学号</td><td>字符</td><td>10</td><td>PK</td></tr><tr><td height="19">c_id</td><td>课程编号</td><td>字符</td><td>10</td><td>Not Null</td></tr><tr><td height="19">score</td><td>成绩</td><td>数值</td><td>3</td><td>Not Null</td></tr></tbody></table>

### 查询 “001” 课程比 “002” 课程成绩高的所有学生的学号；

```sql
	select a.s_id from (select s_id,score from SC where C_ID='001') a,(select s_id,scorefrom SC where C_ID='002') b where a.score>b.score and a.s_id=b.s_id;
```

### 查询平均成绩大于 60 分的同学的学号和平均成绩；

```sql
	select S_ID,avg(score) from sc group by S_ID having avg(score) >60;
```

### 查询所有同学的学号、姓名、选课数、总成绩；

```sql
	select Student.S_ID,Student.Sname,count(SC.C_ID),sum(score) from Student left Outer join SC on Student.S_ID=SC.S_ID group by Student.S_ID,Sname
```

### 查询姓 “李” 的老师的个数；

```sql
	select count(distinct(Tname)) from Teacher where Tname like '李%';
```

### 查询所有课程成绩小于 60 分的同学的学号、姓名；

```sql
	select S_ID,Sname from Student where S_ID not in (select S.S_ID from Student AS S,SC where S.S_ID=SC.S_ID and score>60);
```

### 查询至少有一门课与学号为 “1001” 的同学所学相同的同学的学号和姓名；

```sql
	select distinct S_ID,Sname from Student,SC where Student.S_ID=SC.S_ID and SC.C_ID in (select C_ID from SC where S_ID='1001');
```

JavaScript 语言和 jQuery 技术
------------------------

### JS 中如何将页面重定向到另一个页面？

1.  使用 location.href：window.location.href =”https://www.baidu.com/”
2.  使用 location.replace：window.location.replace (“https://www.baidu.com/;”);

### undefined，null 和 undeclared 有什么区别？

1.  undefined 表示” 缺少值”，就是此处应该有一个值，但是还没有定义，转为数值时为 NaN。典型用法是：变量被声明了，但没有赋值时，就等于 undefined。调用函数时，应该提供的参数没有提供，该参数等于 undefined。对象没有赋值的属性，该属性的值为 undefined。函数没有返回值时，默认返回 undefined。
2.  null 表示” 没有对象”，即该处不应该有值，转为数值时为 0。典型用法是：作为函数的参数，表示该函数的参数不是对象。作为对象原型链的终点。
3.  undeclared：js 语法错误，没有申明直接使用，js 无法找到对应的上下文。

### 如何在 JavaScript 中每 x 秒调用一个函数？

```
	setInterval(function (){ alert("Hello"); }, 3000);
```

### JS 中 == 和 === 区别是什么？

1.  对于 string,number 等基础类型，== 和 === 有区别：不同类型间比较，== 之比较 “转化成同一类型后的值” 看 “值” 是否相等，=== 如 果类型不同，其结果就是不等。同类型比较，直接进行 “值” 比较，两者结果一样。
2.  对于 Array,Object 等高级类型，== 和 === 没有区别，进行 “指针地址” 比较。

### JavaScript 内置可用类型

string，number，boolean，null 和 undefined，object，symbol（ES6 新语法）

### jQuery 库中的 $() 是什么？

$() 函数是 jQuery () 函数的别称。$() 函数用于将任何对象包裹成 jQuery 对象，接着你就被允许调用定义在 jQuery 对象上的多个不同方法。你可以将一个选择器字符串传入 $() 函数，它会返回一个包含所有匹配的 DOM 元素数组的 jQuery 对象。

### jQuery 有几种选择器？

1.  基本选择器：`#id`，`class`,`element`，`*`;
2.  层次选择器：`parent > child`，`prev + next` ，`prev ~ siblings`
3.  基本过滤器选择器：`:first`，`:last` ，`:not` ，`:even`
4.  表单选择器： `:input` ，`:text` ，`:password` ，`:radio` ，`:checkbox` ，`:submit` 等；
5.  表单过滤器选择器：`:enabled` ，`:disabled` ，`:checked` ，`:selected`

### jQuery 中 $.get () 提交和 $.post () 提交有区别吗？

相同点：都是异步请求的方式来获取服务端的数据；

异同点：

*   请求方式不同：$.get () 方法使用 GET 方法来进行异步请求的。$.post () 方法使用 POST 方法来进行异步请求的。
*   参数传递方式不同：get 请求会将参数跟在 URL 后进行传递，而 POST 请求则是作为 HTTP 消息的实体内容发送给 Web 服务器的，这种传递是对用户不可见的。
*   数据传输大小不同：get 方式传输的数据大小不能超过 2KB 而 POST 要大的多
*   安全问题： GET 方式请求的数据会被浏览器缓存起来，因此有安全问题。

### window.onload () 函数和 jQuery 中的 document.ready () 有什么区别？

1.  执行时间：window.onload 必须等到页面内包括图片的所有元素加载完毕后才能执行。$(document).ready () 是 DOM 结构绘制完毕后就执行，不必等到加载完毕。$(document).ready () 在 window.onload 之前执行。
2.  简化写法：window.onload 没有简化写法。$(document).ready (function (){}) 可以简写成 $(function (){});
3.  出现地方不同：window.onload 是 js 标准，可出现在任何 js 脚本中。$(document).ready 只有在 jq 库中出现。

### 什么是 CDN？哪些是流行的 jQuery CDN？使用 CDN 有什么好处？

内容传送网络或内容分发网络（CDN）是部署在因特网上的多个数据中心的大型分布式服务器系统。CDN 的目标是为具有高可用性和高性能的最终用户提供内容。

有 3 个流行的 jQuery CDN：谷歌，微软 jQuery。

使用 CDN 的优势：它减少了服务器的负载。它节省了带宽。jQuery 框架将从这些 CDN 加载更快。最重要的好处是，如果用户访  
问过使用任何这些 CDN 的 jQuery 框架的任何站点，它将被缓存

### 如何从 CDN 加载 jQuery？

下面是从 3 个 CDN 加载 jQuery 的代码。

*   从 Google CDN 加载 jQuery Framework 的代码

```
	 <script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
```

*   从 Microsoft CDN 加载 jQuery Framework 的代码

```
	 <script type="text/javascript" src="http://ajax.microsoft.com/ajax/jquery/jquery-1.9.1.min.js"> </script>
```

*   从 jQuery 站点加载 jQuery Framework 的代码（EdgeCast CDN）

```
	 <script type="text/javascript" src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
```

JSP 技术
------

### 说一说 Servlet 的生命周期？

1.  Servlet 有良好的生存期的定义，包括加载和实例化、初始化、处理请求以及服务结束。这个生存期由 javax.servlet.Servlet 接口的 init (),service () 和 destroy 方法表达。
2.  Servlet 被服务器实例化后，容器运行其 init 方法，请求到达时运行其 service 方法，service 方法自动派遣运行与请求对应的 do\*\*\*() 方法（doGet，doPost）等，当服务器决定将实例销毁的时候调用其 destroy 方法。
3.  web 容器加载 servlet，生命周期开始。通过调用 servlet 的 init () 方法进行 servlet 的初始化。通过调用 service () 方法实现，根据请求的不同调用不同的 do\*\*\*() 方法。结束服务，web 容器调用 servlet 的 destroy () 方法。

### jsp 和 servlet 的区别、共同点、各自应用的范围？

JSP 是 Servlet 技术的扩展，本质上就是 Servlet 的简易方式。JSP 编译后是 “类 servlet”。Servlet 和 JSP 最主要的不同点在于：Servlet 的应用逻辑是在 Java 文件中，并且完全从表示层中的 HTML 里分离开来。而 JSP 的情况是 Java 和 HTML 可以组合成一个扩展名为.jsp 的文件。JSP 侧重于视图，Servlet 主要用于控制逻辑。在 struts 框架中，JSP 位于 MVC 设计模式的视图层，而 Servlet 位于 控制层.

### Servlet API 中 forward () 与 redirect () 的区别？

*   从地址栏显示来说

forward 是服务器请求资源，服务器直接访问目标地址的 URL, 把那个 URL 的响应内容读取过来，然后把这些内容再发给浏览器。浏览器根本不知道服务器发送的内容从哪里来的，所以它的地址栏还是原来的地址. redirect 是服务端根据逻辑，发送一个状态码，告诉浏览器重新去请求那个地址。所以地址栏显示的是新的 URL. 所以 redirect 等于客 户端向服务器端发出两次 request，同时也接受两次 response。

*   从数据共享来说

forward: 转发页面和转发到的页面可以共享 request 里面的数据.redirect: 不能共享数据.redirect 不仅可以重定向到当前应用程序的其他资源，还可以重定向到同一个站点上的其他应用程序中的资源，甚至是使用绝对 URL 重定向到其他站点的资源.forward 方法 只能在同一个 Web 应用程序内的资源之间转发请求.forward 是服务器内部的一种操作.redirect 是服务器通知客户端，让客户端重新发起请求。所以，你可以说 redirect 是一种间接的请求，但是你不能说” 一个请求是属于 forward 还是 redirect “。

*   从运用地方来说

forward: 一般用于用户登陆的时候，根据角色转发到相应的模块. redirect: 一般用于用户注销登陆时返回主页面和跳转到其它的网站等。

*   从效率来说

forward: 高。

redirect: 低。
