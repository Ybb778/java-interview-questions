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