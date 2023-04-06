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

```sql
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

```sql
	select 学号，姓名 from Student where 学号 in（select 学号 from Sc where 课程编号 in(Select 课程编号 from Course where 课程名称 = ‘计算机原理’)）
```

*   写一个 SQL 语句，查询 “周星驰” 同学选修了的课程名字

```sql
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
