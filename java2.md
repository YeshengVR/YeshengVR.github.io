# Java二期

## 网络编程

### UDP：用户数据协议

面向无连接通信协议，限制传输数据在64kb之内，传输时数据可能丢失。传输效率高，速度快，但是可能会丢失数据包。（通常用于音频、视频、普通数据传输）

### TCP：传输控制协议

TCP是面向连接的通信协议，在传输数据之前在发送端和接收端建立逻辑链接，然后再传输数据。其提供了两台计算机之间可靠无差错的数据传输。

#### 三次握手

- 第一次握手：客户端向服务器发出连接请求，等待服务器确认。
- 第二次握手：服务器端向客户端回送一个响应，通知客户端收到了连接请求。
- 第三次握手：客户端再次向服务器发送确认信息，确认链接。

TCP通信能实现两台计算机之间的数据交互，通信的两端，严格区分为客户端与服务端。

#### 通信两步骤

1. 服务器程序，需要事先启动，等待客户端的连接。
2. 客户端主动连接服务器端，连接成功才能通信，服务端不可以主动连接客户端。

![](F:\md笔记文件\javaimg\TCP通信.jpg)

### 实现TCP通信程序

1. 客户端：java.net.Socket类表示。创建Socket对象，向服务器发出连接请求，服务器响应请求，两者建立连接开始通信。
2. 服务器：java.net.ServerSocket类表示。创建SeverSocket对象，相当于开启一个服务，并等待客户端的连接。

### Socket类

Socket类：该类实现客户端套接字，套接字指的是两台设备之间通讯的端点。

### 协议

计算机通信必须遵守的规则。

### IP地址

互联网协议地址俗称IP地址

IPv4：4个32位的二进制数

IPv6：8组16进制数

表示本机地址

查询ip命令：

```cmd
ipconfig
```

## 数据库

存储大量数据，方便访问和检索

##### 数据库物理结构

**数据文件：**

扩展名是.DBF,用于存储数据库数据的文件

数据库表和数据文件不存在一对一对应关系。

**控制文件：**

扩展名是.CTL，是数据库启动及运行所必需的文件

默认包含3个控制文件，各个控制文件内容相同

**日志文件：**

扩展名是.LOG,它记录了对数据的所有更改信息

多个日志文件组之间

##### 数据库逻辑结构

**表空间：**

每个Oracle数据库都是由若干个表空间构成，用户在数据库中建立的所有内容都被存储到表空间中

创建数据库时会自动创建若干表空间

**应用程序：**

作用：响应操作并显示结果、向数据库请求数据

要求：美观、操作简单方便。

**数据库：**

作用：存储数据、检索数据、生成新的数据

要求：统一，安全、性能等。

数据库： 永久的，硬盘上

数据库实例：临时的，内存上。

1. 数据库的英文单词： DataBase 简称 ： DB
2. 什么数据库？
	* 用于存储和管理数据的仓库。
3. 数据库的特点：
	1. 持久化存储数据的。其实数据库就是一个文件系统
	2. 方便存储和管理数据
	3. 使用了统一的方式操作数据库 -- SQL

角色是具有名称的一组权限的组合。

```
常用系统预定于角色
CONNECT：临时用户
RESOURCE：更为可靠和正式的用户
DBA：数据库管理员角色，拥有管理数据库的最高权限
```

#### **Oracle数据类型**

```
char():存储固定长度的字符串。
var char2():存储可变长度的字符串。
nchar(和nvarchar2():存储Unicode字符集类型
```

```
number:存储整数和浮点数，格式为number(p,s)
number:	(p=38,s=0)
number(p): (整数最大有p位)
number(p,s):	(总共最多可以有p位，整数最多有p-s位，小数至少有s位)
```

```
日期时间数据类型
date:存储日期和时间数据
timestamp：比date更精确。
```

```
lob数据类型
blob：存储二进制对象，如图像、音频和视频文件
clob：存储字符格式的大型对象。
```



#### 数据完整性

选择不会更新的列作为主键。

可靠性+准确性=数据完整性

创建表：保证数据的完整性=实施完整性约束

```sql

-- 可靠性 + 准确性 = 数据完整性
-- 保证数据的完整性 = 实施完整性约束
-- 域完整性：
/*
   表中特定列数据的有效性，确保不会输入无效的值
   实现方式：类型、缺省值、检查、空值,外键
*/

-- 实体完整性：
/* 
   唯一约束: 通过给字段添加Unique约束。
   主键约束：能唯一标识一行记录的字段。则可以将该字段设置为主键。Primary主键
   <唯一约束可以为null；主键约束不可以为null。>
   标识列：用以标识一个实体的列，该标识列与实体属性无关。
   (一般标识列都是唯一的，且当作主键)
*/
-- 引用完整性：
/*
    维护表间数据的有效性、完整性
    实现方式：建立外键联系另一表的主键
*/
-- 自定义完整性：
/*
   根据业务处理流程定义的特定业务规则
   实现方式：存储过程、触发器、规则
*/
```

##### 主键约束

主键用于唯一的标识表中的每一条记录

可以定义一列或多列为主键

主键列上没有任何两行具有相同值

主键列上也不能为空值

##### 唯一性约束

唯一性约束用来限制不受主键约束的列上的数据的唯一性，一个表上可以放置多个唯一性约束，

唯一性约束可以有null值。

*在创建唯一性约束和主键约束时可以创建聚集索引和非聚集索引，但在默认情况下主键约束产生聚集索引，二唯一性约束产生非聚集性索引*

##### 检查约束

检查约束用来指定某列的可取值的范围

它通过限制输入到列中的值来强制域得得完整性。

##### 默认约束

默认约束用于给表中的指定列赋予一个常量值（默认值），党项该表插入数据时，如果用户没有明确给出该列的值，则会自动为该列输入默认值。（SQL Sever）每列只能有一个默认约束。

##### 外键约束

外键约束用于与其他表（称为参照表）中的列（称为参照列）建立连接。
  将参照表中的主键所在列或具有唯一性约束的列包含在另一个表中，这些列就   构成了另一个表的外键。
  当参照表中的参照列更新后，外键列也会自动更新，  从而保证两个表之间的  一致性关系。
   注意：(1).将“强制外键约束”或"强制用于复制”设置为“是”，能确保任何数据添加、修改或删除操作都不会违背外键关系
           (2).将“更新规则”或"删除规则”设置为“无操作”，拒绝更新或删除主键表
              将“更新规则”或"删除规则”设置为“层叠”，级联更新或删除从表中相应的所有行
              将“更新规则”或"删除规则”设置为“设置空”，将外键表中相对应的外 键值设置为空值NULL
              将“更新规则”或"删除规则”设置为“设置默认值”，如果外键表的所有外键列均已定义默 认值，则该列设置为默认值

### SQL

sql语言对大小写不敏感。

SQL的查询规则：先找表（执行from 表名），在判断条件（where 条件），再来查找（select）。

```sql
--Sql语言的组成

--DML： date Manipulation language 数据管理语言
--insert update delete
--插入、删除修改数据库中的数据

--DQL： date Query language       数据查询语言
--select
--查询

--DDL： date defined language     数据定义语言
--crate table、drop table
--建表、删表

--DCL： date controler language   数据控制语言
--grant、revore
--用来控制许可、存储权限等
```



```
1.什么是SQL？
	Structured Query Language：结构化查询语言
	其实就是定义了操作所有关系型数据库的规则。每一种数据库操作的方式存在不一样的地方，称为“方言”。
	
2.SQL通用语法
	1. SQL 语句可以单行或多行书写，以分号结尾。
	2. 可使用空格和缩进来增强语句的可读性。
	3. MySQL 数据库的 SQL 语句不区分大小写，关键字建议使用大写。
	4. 3 种注释
		* 单行注释: -- 注释内容 或 # 注释内容(mysql 特有) 
		* 多行注释: /* 注释 */
	
3. SQL分类
	1) DDL(Data Definition Language)数据定义语言
		用来定义数据库对象：数据库，表，列等。关键字：create, drop,alter 等
	2) DML(Data Manipulation Language)数据操作语言
		用来对数据库中表的数据进行增删改。关键字：insert, delete, update 等
	3) DQL(Data Query Language)数据查询语言
		用来查询数据库中表的记录(数据)。关键字：select, where 等
	4) DCL(Data Control Language)数据控制语言(了解)
		用来定义数据库的访问权限和安全级别，及创建用户。关键字：GRANT， REVOKE 等
```

#### SQL的运算符

##### 算术运算符

| 运算符 | 说明                                   |
| ------ | -------------------------------------- |
| +      | 加运算，求两个数或表达式相加的和       |
| -      | 减运算，求两个数或表达式相减的差       |
| *      | 乘运算，求两个数或表达式相乘的积       |
| /      | 除运算，求两个数或表达式相除的商       |
| mod    | 取模运算，求两个数或表达式相除的余数。 |

##### 赋值运算符

| 运算符 | 说明                                 |
| ------ | ------------------------------------ |
| =      | 把一个数或变量或表达式赋值给另一变量 |

##### 逻辑运算符

| 运算符 | 说明                                       |
| ------ | ------------------------------------------ |
| AND    | 当且仅当两个布尔表达式都为true时，返回true |
| OR     | 当且仅当两个布尔表达式都为false，返回false |
| NOT    | 对布尔表达式的值取反                       |

##### 比较运算符

| 运算符 | 说明                   |
| ------ | ---------------------- |
| **=**  | 等于                   |
| **>**  | 大于                   |
| **<**  | 小于                   |
| **<>** | 不等于                 |
| **>=** | 大于等于               |
| **<=** | 小于等于               |
| **!=** | 不等于（非SQL-92标准） |

### 插入数据行语句

```sql
--插入数据行语句
insert into 表名 [(列名)] values (值列表)
/*Example：
INSERT INTO Students (SName,SAddress,SGrade,SEmail,SSEX) 
VALUES ('张青裁','上海江',6,'ZQC@Sohu.com',0)
*/
```

注意事项：

- 每次插入一行数据，不能只插入半行或者几行数据。插入的数据是否有效将按照整行的 完整性的要求来检验。
- 每个数据值的数据类型、精度和小数位数必须与相应的列匹配
- 如果在设计表的时候就指定了某列不允许为空，则必须插入数据。
- 插入的数据项，要求符合检查约束的要求
- 具有缺省值的列，可以使用default（缺省）关键字来代替插入的数值。

### 插入多行数据

方法一：

通过insert select 语句将现有表中的数据添加到已存在的表中。

```sql
insert into <表名>(列名) select<列名> from<源表名>
/*Example
insert into AddressList(姓名,地址,电子邮件) 
SELECT 	SName,SAddress,SEmail FROM Students
*/
```

方法二：

通过create table 语句将现有表中的数据添加到新表中。

```sql
create table<表名> as select <列> from<源表名>
/*EXample
create table B as select * from S
*/
```

方法三：

通过union关键字合并数据进行插入

```sql
--第三种方案：
insert into 表名1 [(字段1,字段2,...)]
select 值1,值2,... from dual 
union
select 值1,值2,... from dual 
union
...;

insert all into
表名1[(字段1,字段2,...)] values (值1,值2,...)
into
表名1[(字段1,字段2,...)] values (值1,值2,...)
into
表名1[(字段1,字段2,...)] values (值1,值2,...)
...
select * from dual;
……
/*Example
insert into student2
select '1001','aaa',1 from dual 
union
select '1002','bbb',2 from dual 
union
select '1003','ccc',3 from dual;

insert  all into
student2 values ('1004','xxx',1)
into 
student2 values ('1005','yyy',2)
into
student2 values ('1006','zzz',3)
select * from dual;

*/
```

### 更新数据

```sql
update 表名 set 列名 = 更新值 [where 更新条件]
/*Example:
update Students set sex = 0

Example2:
UPDATE Scores SET Scores = Scores + 5
WHERE Scores <= 95
*/
```

### 删除数据

```sql
delete[from] 表名 [where<删除条件>]
/*Example：
delete from Students where SName='张霞'
*/
```

去除重复的关键字：distinct

当前系统时间关键字：sysydate

### 查询语句

```sql
--查询语法：
select [all | distinct] 表达式列表 [as 别名]
          from 表名或者视图名
          [where 条件表达式]
          [group by 列名]
          [having 搜索表达式]
          [order by 列名 [asc | desc]]
```

```sql
/*
Example:
--查询全部性别为男的学生并且是在一班，按年龄来排序
select *
  from student
 where gradeid = 1
   and sex = '男'
 order by borndate desc
*/
```

#### 重命名列as

```sql
select
       studentname as 学生姓名,
       borndate as "出生 日期"
from student;
```

如果别名中有特殊字符，可以使用双引号。

as放在select查询的列中可进行重命名。

如果要重命名表则不需要添加as ,添加as反而会报错***ORA-00933: SQL command not properly ended***

```sql
select * from student stu where stu.name = '张三';
```

**查询空行**，查询某一个字段值为空的行

```sql
select * from student where email is null or email = '';
```

#### 限制行数rownum

```sql
--限制行数：分页

--查询前两条学生信息
select * from student where rownum <= 2;
--查询3~4的数据
select *
  from (select rownum as rn, student.* from student where rownum <= 4) t
 where t.rn >= 3;
```

错误的书写方式

```sql
select rownum,student.* from student where rownum <= 4 and rownum > 2;
--rownum不能大于值(不能写rownum>XXX,因为sql是逐行读取数据的，使用rownum>某个值时，不符合条件就会排除掉这个元素，然后每次读取时就都不会满足条件。故不能书写rownum>n)
```

```sql
 /*多表连接查询*/
 --查询学生中email为空的学生班级名称。
 select studentname, g.gradeid, gradename
   from student s, grade g
  where s.gradeid = g.gradeid
    and (email is null or email = '');
```

#### 排列 order by

排列中的列可以用表达式。

**升序排列**

排序是通过order by关键字，order by关键字放在where条件后面,order by执行顺序在select后面

asc是升序排列

```sql
order by 字段.... [asc \ desc]
```

**降序排列**

desc是降序排列

如果遇到两个排序条件，先执行第一个排序队列，再在第一个基础上执行后一个排序条件。

#### case when then

Case具有两种格式。简单Case函数和Case搜索函数。

```sql
--简单Case函数
CASE sex
         WHEN '1' THEN '男'
         WHEN '2' THEN '女'
ELSE '其他' END
--Case搜索函数
CASE WHEN sex = '1' THEN '男'
         WHEN sex = '2' THEN '女'
ELSE '其他' END
```

CASE
  WHEN 条件1 THEN 结果1
  WHEN 条件2 THEN 结果2
  WHEN 条件3 THEN 结果3
  WHEN 条件4 THEN 结果4
.........
  WHEN 条件N THEN 结果N
  ELSE 结果X
END

```sql
case when ：当......
```

#### 模糊查询

like：像...

通配符：**%匹配任意个字符；_匹配一个字符**

```sql
查询姓张的学生
select * from student where studentname like'张%'
```

```sql
not like
--查询非姓张的学生
select * from student where studentname not like'张%'
```

为空is null



在.....之间：between   

注意：between 第一个值比第二个值要小。

```sql
--查询年龄年龄在18到20之间的男学生信息
select * from student where age between 18 and 20 and sex = '男';
```

in：查询某一列中内容与所列出的内容列表匹配的记录

```sql
select * from student where gradeid = 1 or gradeid = 5;
select * from student where gradeid in (1,5);
```

#### 分组查询group by

```sql
select ...... from <表名> where .... group by
```

这条语句的执行顺序：from->where->group by ->select

例如

| student | subject | results |
| ------- | ------- | ------- |
| 赵四    | java    | 72      |
| 赵四    | Oracle  | 88      |
| 张三    | html    | 90      |
| 张三    | java    | 78      |
| 王五    | java    | 92      |

```sql
select student, sum(results)
  from C
 where subject <> 'Oracle'
 group by student
```

查询 C表中的 subject不为Oracle的数据并按照student来进行分组，查询每个学生的成绩综合。

注意：输出的字段必须得是通过group by分组的字段，或者通过聚合函数获得的数据。否则会报错ORA-00979: not a GROUP BY expression

如果group by 后面跟随的是多个字段的话，分组顺序是按照group by后面的字段顺序依次分组；为了书写规范化，建议输出字段的顺序group by子句中字段的顺序要保持一致
**group by all 语句**
group by的后面加上一个all，表示对通过where子句查询得到的结果集进行分组查询后，依然显示被where子句过滤掉的记录，但是其他通过聚合函数统计的数据都会显示0或null。
**group by with cube**
GROUP BY 后面加上CUBE运算符后，结果集会在GROUP BY分组统计的结果集基础上，增加归纳各个单独字段和相互混合字段后统计得到的多维交叉结果集。
GROUP BY 后面加上CUBE运算符后，结果集会在GROUP BY分组统计的结果集基础上，增加归纳各个单独字段和相互混合字段后统计得到的多维交叉结果集。
**group by with rollup**
ROLLUP与CUBE作用一样，都是在GROUP BY的基础上，进一步归纳统计数据，但是ROLLUP比CUBE的限制要多。它不会将所有的字段混合归纳，而是根据GROUP BY后面字段的顺序，从高等级字段向低等级字段归纳，因此GROUP BY后面字段的顺序会影响分组结果。

##### having

分组过滤

having用法和where是基本相同的，都是作用于限制条件的。having的作用范围是在group by的分组中，而where则是在整个表中。

```sql
select ... from ... where ... group by ... having ... order by ....
```

执行顺序：where > group by > having > order by; 

#### 多表连接查询

多表连接的on后面跟随的是连接的条件。

- 内连接（inner join）

内连接在书写时可以省略inner，不过为了书写规范，能一眼就看出是什么连接，最好写上去。

内连接中，连接的行数是根据最少方的，查询到那个为null就结束了。两者表都有的，结果集才有。

```sql
/*Example
select s.name, c.courseid, c.score
  from score as c
 inner join students as s
    on c.studentid = s.studentid;
    等价于
select s.name, c.courseid, c.score
  from score as c, students as s
 where c.studentid = s.studentid;
*/
```

- 外连接

  - 左外连接（left join）

  左外连接：返回左表中的所有行，如果左表中行在右表中没有匹配行，则在相关联的结果集中右表的所选择字段均为NULL。

  以左表为主表，左边表中有的数据结果集中就一定有。

  **LEFT [OUTER] JOIN**

  - 右外连接（right join）
  

返回右表中的所有行，如果右表中行在左表中没有匹配行，则在左表中相关字段返回NULL值。 

以右表为主表，右边表中有的数据结果集中就一定有。

**RIGHT [OUTER] JOIN**

  主从表位置交换的话，结果也会随之变化。

  - 全外连接/完全外连接

  返回两个连接中所有的记录数据，是左外连接和右外连接的并集。 

  两边有的全部都要。

  **FULL [OUTER] JOIN**

  - 交叉连接/笛卡尔积

  两个表做笛卡尔积，得到的结果集的行数是两个表的行数的乘积。 
  **CROSS JOIN**

 注意：带有where条件的子句，往往会先生成两个表行数乘积的数据表，然后从根据where条件从中选择。 

#### 子查询

子查询在WHERE语句中的一般用法：
子查询总是用小括号括起来。    
将子查询和比较运算符联合使用，必须保证子查询返回的值不能多于一个。

子查询是一个嵌套在 SELECT、INSERT、UPDATE 或 DELETE 语句或其他子查询中的查询

有关子查询语句的执行顺序，首先执行小括号中的子查询，返回的结果是所有来自子查询的结果。其次，才开始执行外围的父查询，返回查询的最终结果。

```sql
/*Example
--查询年龄比“李斯文” 大的学生
select studentno, studentname
  from student
 where borndate > 
       (select borndate 
          from student
         where studentname = '李斯文');
*/
```

一般来说表连接都可以用子查询替换，但有的子查询却不能用表联接替换。

子查询比较灵活，方便，常作为增删改查的筛选条件，适合于操纵一个表的数据。表连接更适合于查看多表的数据。

##### in子查询

in后面的子查询可以返回多条记录，常用in替换（=）的比较子查询。

查询结果为多行单列的使用运算符in来判断。

查询结果为多行多列的，子查询可以作为一张虚拟表参与查询。

一般的类似报出错误**ORA-01427**: single-row subquery returns more than one row，可以使用将判断条件的（=）改变成（in）

```sql
/*Example
--查询未参加“Java Logic”课程考试的学生名单
select *
  from student
 where results.studentno not in
       (select studentno
          from results
         where subjectid in (select subjectid
                               from subject
                              where subjectname = 'Java Logic'));
*/
```

当使用**in**表达时通常的只需要前面的字段有一个符合后面的字段就可以。

相应的 not in 表达式只要有一个前面的字段匹配上后面的字段就不行。

**注意**：

- 任何允许使用表达式的地方都可以使用子查询
- 嵌套在父查询select语句的子查询可包括：
  1. select子句
  2. from子句
  3. where子句
  4. group by子句
  5. having 子句
- 子出现在子查询中而没有出现在父查询中的表不能包含在输出列中。

#### 递归查询

Oracle 中是通过 start with connect by prior 语法来实现递归查询的。

按照 prior 关键字在子节点端还是父节点端，以及是否包含当前查询的节点，共分为四种情况。

**prior 在子节点端（向下递归）**

**第一种情况**： start with 子节点id = ' 查询节点 ' connect by prior 子节点id = 父节点id

```sql
--Example：
select * from dept start with id='1001' connet by prior id=pid;
```

![](F:\md笔记文件\javaimg\递归查询1.jpg)

**第二种情况**： start with 父节点id= ' 查询节点 ' connect by prior 子节点id = 父节点 id

```sql
select * from dept start with pid='1001' connect by prior id=pid;
```

这里，按照条件 pid='1001' 对当前节点的所有子节点递归查询。查询结果只包含它的所有子节点，**不包含自己**。

![](F:\md笔记文件\javaimg\递归查询2.jpg)

**prior 在父节点端（向上递归）**

第三种情况： start with 子节点id= ' 查询节点 ' connect by prior 父节点id = 子节点id

```sql
select * from dept start with id='1001' connect by prior pid=id;
```

这里按照条件 id='1001' ，对当前节点及其父节点递归查询。查询结果**包括自己**及其所有父节点。

![](F:\md笔记文件\javaimg\递归查询3.jpg)

**第四种情况**： start with 父节点id= ' 查询节点 ' connect by prior 父节点id = 子节点id

```sql
select * from dept start with pid='1001' connect by prior pid=id;
```

这里按照条件 pid='1001'，对当前节点的第一代子节点以及它的父节点递归查询。查询结果包括自己的第一代子节点以及所有父节点。（**包括自己**）

![](F:\md笔记文件\javaimg\递归查询4.jpg)

我们只需要记住 **prior 的位置在子节点端，就向下递归，在父节点端就向上递归。**

- 开始条件若是子节点的话，自然包括它本身的节点。
- 开始条件若是父节点的话，则向下递归时，自然不包括当前节点。而向上递归，需要包括当前节点及其第一代子节点。

### 聚合函数

对一组数据进行计算，并返回计算后的值，具有统计数据的作用。

聚合函数通常会在下列场合使用：
1、select语句的选择列表，包括子查询和外部查询。
2、使用compute或compute by产生汇总列时。
3、having子句对分组的数据记录进行条件筛选。

```sql
--sum():求和
select sum(字段) from result
```

```sql
--avg():求平均
select avg(字段) from result
```

```sql
--count():求个数
select count(*) from result where 字段 is not null
```

count(1)和count(*)相比，count(1)效率更高。

```sql
--max():求最大值
select max(字段) from result
```

```sql
--min():求最小值
select min(字段) from result
```

### Oracle常用函数

Oracle函数划分为单行函数和多行函数。

单行函数作用于数据库表的某一行并返回一个值

- 字符函数
- 数字函数
- 日期函数
- 转换函数
- 其他函数

#### 常用的字符函数：

> 基本上每一种函数都需要参数。

initcap（char）：首字母转大写

```sql
select initcap('hello') from dual
```

lower(char)：转小写

```sql
select lower('hello') from dual
```

upper(char):转大写

```sql
select upper(字段)from 表名
```

ltrim(char,set)：左裁减

```sql
select ltrim(字段，'替换值')from 表名
```

rtrim(char,set):右裁剪

```sql
select rtrim(字段，'替换值')from 表名
```

ps：左右裁剪必须对应着开头或者末尾，不能是在中间，否则裁剪不了。

TRANSLATE(char,from,to):按字符顺序翻译

```sql
select TRANSLATE(字段,'字符','字符对应值') from 表名
例如：select studentno,translate(loginpwd,'12345zh','abcdef12') from student
原始值：1236h54z，变更值为：abcf2ed1
```

replace(char,search_char,replace_str):字符串替换

```sql
select replace(字段,'查找的字符串','替换的字符串') from 表名
```

instr(char,substr[,pos])：查找子串位置

```sql
select instr(字段,'要找的值'[,n]) from 表名
--中括号里面可有可不有，有就从n开始找，没有就从开始开始找。
```

substr(char,pos,len):截取子串

```sql
select substr(字段，截取的位置，长度) from 表名
```

 concat(str1,str2):连接字符串

```sql
select concat(字段，字段) from 表名
```

ps：Oracle中两列，两行合并可以这样操作

```sql
select 字段||','||字段 from 表名--列合并
```

```sql
select 字段1，listagg(to_char(字段2),',') with in group(order by 字段1) as 字段名  from 表名
group by 字段1 --行合并
```

#### 常用的数字函数：

| **函 数**       | **功 能**          | **示 例**            | **结 果**      |
| --------------- | ------------------ | -------------------- | -------------- |
| **ABS(n)**      | **取绝对值**       | **abs(-15)**         | **15**         |
| **CEIL(n )**    | **向上取整**       | **ceil(44.778)**     | **45**         |
| **SIN(n)**      | **正弦**           | **sin(1.571)**       | **.999999979** |
| **COS(n)**      | **余弦**           | **cos(0)**           | **1**          |
| **SIGN(n)**     | **取符号**         | **sign(-32)**        | **-1**         |
| **FLOOR(n)**    | **向下取整**       | **floor(100.2)**     | **100**        |
| **POWER(m,n )** | **m****的**n**次幂 | **power(4,2)**       | **16**         |
| **MOD(m,n)**    | **取余数**         | **mod(10,3)**        | **1**          |
| **ROUND(m,n)**  | **四舍五入**       | **round(100.256,2)** | **100.26**     |
| **TRUNC(m,n)**  | **截断**           | **trunk(100.256,2)** | **100.25**     |
| **SQRT(n)**     | **平方根**         | **sqrt(4)**          | **2**          |

#### 常用的日期函数：

| **函 数**          | **功 能**                            | **示 例**                                                    | **结 果**                                                    |
| ------------------ | ------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **sysdate**        | **返回系统日期**                     | **sysdate**                                                  | **2014-6-11 14:01:11**                                       |
| **extract**        | **从 date型字段中抽取某一部分内容**  | **extract(year from sysdate)\|\|'****年****'\|\|extract(month from sysdate)\|\|'****月****'** | **2014年6月**                                                |
| **MONTHS_BETWEEN** | **返回两个日期间的月份**             | **months_between ('04-11****月****-05','11-1****月****-01')** | **57.7741935**                                               |
| **ADD_MONTHS**     | **返回把月份数加到日期上的新日期**   | **add_months('06-2****月****-03',1)****add_months('06-2****月****-03',-1)** | **06-3****月****-03****06-1****月****-03**                   |
| **NEXT_DAY**       | **返回指定日期后的星期对应的新日期** | **next_day('06-2****月****-03','****星期一****')**           | **10-2****月****-03**                                        |
| **LAST_DAY**       | **返回指定日期所在的月的最后一天**   | **last_day('06-2****月****-03')**                            | **28-2****月****-03**                                        |
| **ROUND**          | **按指定格式对日期进行四舍五入**     | **round(to_date('13-2****月****-03'),'YEAR')** **round(to_date('13-2****月****-03'),'MONTH')****round(to_date('13-2****月****-03'),'DAY')** | **01-1****月****-03****01-2****月****-03****16-2****月****-03** |
| **TRUNC**          | **对日期按指定方式进行截断**         | **trunc(to_date('06-2****月****-03'),'YEAR')****trunc(to_date('06-2****月****-03'),'MONTH')****trunc(to_date('06-2****月****-03'),'DAY')** | **01-1****月****-03****01-2****月****-03****02-2****月****-03** |

#### 常用的转换函数：

| **函 数**     | **功 能**            | **示 例**                                       | **结 果**             |
| ------------- | -------------------- | ----------------------------------------------- | --------------------- |
| **TO_CHAR**   | **转换成字符串类型** | **to_char(1234.5, '$9999.9')**                  | **$1234.5**           |
| **TO_DATE**   | **转换成日期类型**   | **to_date('1980-01-01',**     **'yyyy-mm-dd')** | **01-1****月****-80** |
| **TO_NUMBER** | **转换成数值类型**   | **to_number('1234.5')**                         | **1234.5**            |

to_char将数字转换成字符串，的格式里只能填写0或者9并且，必须转换的位数得超过本来数字的位数长度。否则查出来会都是####

```sql
select to_char(123456.789,'9,999,999.99') from dual
```



#### 常用的其他函数：

| **函 数**                                         | **功 能**                                                    |
| :------------------------------------------------ | ------------------------------------------------------------ |
| **NVL(EXP1, EXP2)**                               | **如果****exp1****的值为****null****，则返回****exp2****的值，否则返回****exp1****的值** |
| **NVL2(EXP1, EXP2, EXP3)**                        | **如果****exp1****的值为****null****，则返回****exp3****的值，否则返回****exp2****的值** |
| **DECODE(VALUE,IF1,THEN1,****IF2,THEN2,……,ELSE)** | **如果****value****的值为****if1****，则返回****then1****的值，如果****value****的值为****if2****，则返回****then2****的值，****……****，否则返回****else****值** |



多行函数基于数据库表多行进行运算，并返回一个值。

| **函 数**   | **功 能**    | **示 例**                                              |
| ----------- | ------------ | ------------------------------------------------------ |
| **SUM()**   | **求和**     | **select sum(love) from pet;**                         |
| **AVG()**   | **求平均值** | **select avg(health) from pet** **where master_id=1;** |
| **COUNT()** | **计数**     | **select count(type_id) from pet;**                    |
| **MAX()**   | **求最大值** | **select max(adopt_time) from pet;**                   |
| **MIN()**   | **求最小值** | **select min(adopt_time) from pet where type_id=1;**   |

adopt：收养时间

### DDL

数据定义语言 data declare langurage

创建表的基本步骤

确定表中有哪些列，确定没列的数据类型，给表添加各种约束，创建各表之间的关系。

```sql
create table tablename(
	fieldname1 类型	[约束],
	fieldname2 类型	[约束],
    ...
)--创建表
drop table tablename;--删除表
```

```sql
create table students 
(
studentno varchar2(20) primary key,--主键约束
loginpwd varchar(20) default '123456',--默认约束
name varchar2(50) not null,--非空约束
sex varchar2(4) check(sex ='男' or sex = '女'),
age number check(age>0 and age<150),--检查约束
phone  varchar2(50) unique --唯一约束
==================================
gradeid number(10) references grade(gradeid)--关联另外一张表的主键/外键约束
gradeid number(10), constraint for_student_gradeid foreign key(gradeid) references grade(gradeid)--两种方式都可创建外键约束
)
```

#### 添加约束的语法

```sql
ALTER TABLE 表名  
     ADD CONSTRAINT 约束名  约束类型  具体的约束说明
/*Example：
alter table students
add constraint Ck_student_loginpwd check(length(loginpwd)>=6);
------------------------
alter table students modify loginpwd(字段名) default '123456';
-----------------
alter table students modify name(字段名) not null
*/
```

约束名的取名规则推荐采用：约束类型_约束列
主键（Primary Key）约束：如 PK_stuNo
唯一（Unique Key）约束：如 UQ_stuID
检查（Check Key）约束：如 CK_stuBornDate
外键（Foreign Key）约束：如 FK_stuNo 

#### 删除约束的语法

```sql
ALTER TABLE 表名  
      DROP CONSTRAINT 约束名 
/*Example:
alter table student
drop constraint Uq_card;
*/
```

**建议**：创建表结构后应立即添加约束，不要马上插入数据，以避免插入的数据不符合约束要求，保证表中数据满足约束限制

#### 修改表名

```sql
alter table tablename rename to tableNewName
```

#### 增加列

```sql
alter table tablename add (字段) 字段类型 [约束]
```

#### 修改列名

```sql
alter table tablename rename column (字段名) to (新字段名)
```

#### 删除列

```sql
alter table tablename drop column (字段);
```

#### 创建索引

通过索引可以提高执行sql语句的效率。建立索引很耗内存，因为索引是直接把整列全部拿出来，如果数据量较小时不建议创建索引。

```sql
--创建索引
create index indexname on tablename (fieldname,....)
/*Example
create index indaddress on student (address)
*/
--删除索引
/*Example
drop index indaddress
*/
```

### PL/SQL语句

PL/SQL（Procedural Language/SQL）
一种过程化语言，通过增加编程语言的特点，实现对SQL的扩展

特点：

- 支持所有SQL的语法
- 支持case语句，方便的实现循环
- 通过继承，实现子类具有父类的属性和方法
- 设置了新的日期类型

PL/SQL的工作原理

- 由PL/SQL引擎接收指令
- 将指令传递给Oracle数据库服务器执行

![](F:\md笔记文件\javaimg\PL_SQL开工作环境.png)

#### 条件控制语句

declare:用于声明变量、游标

变量命名规则

- 变量名首字母必须是英文字母，其后可以是字母、数字或者特殊字符$、#和下划线
- 变量名长度不超过30个字符
- 变量名中不能有空格

>  变量名 类型 [:=值]
>
> 变量名 constant 类型 not null [:=值];

![](F:\md笔记文件\javaimg\PL_SQL声明.png)

声明了常量就必须得赋值。

```plsql
declare --声明，定义

begin -- 开始

[Exception] --当出现异常时的处理

end; --结束 end后面一定要加（;）符号
/*Example
declare 
 i number(10) := 10;
begin
  dbms_output.put_line(i/0);
Exception
  when others then
    dbms_output.put_line('出异常了');
end;
*/
```

##### if-then-elsif：

> **IF condition1 THEN**
>     **Statements1**
> **ELSIF condition2 THEN**
>     **Statements2**
> **ELSE**
>     **Statements3**
> **END IF;**

注意中间的是elsif 不是elseif    ！！

```plsql
declare
i number(10) := 10;
begin
  if i>0 then
    dbms_output.put_Line(i||'大于0');
    end if;
end;
>>>10大于0

declare
i number(10) := 10;
begin
  if i>0 then
    dbms_output.put_Line(i||'大于0');
  elsif i=0 then
    dbms_output.put_line(i||'等于0');
  else
    dbms_output.put_line(i||'小于0');
    end if;
end;
>>>10大于0
```

##### case

> **CASE variable**
>     **WHEN value1 THEN statements1;**
>     **WHEN value2 THEN statements2;**
>     **……**
>     **WHEN valuen THEN statementsn;**
>     **[ELSE else_statements;]**
> **END CASE;**

依据variable表达式，选择相应的when子句执行。与switch非常相似。

```plsql
DECLARE
       grade char:='A';
       remark varchar2(20);
BEGIN
       CASE grade
            WHEN 'A' THEN remark:="is Excellent";
            WHEN 'B' THEN remark:="is Good";
            WHEN 'C' THEN remark:="is Normal";
            WHEN 'D' THEN remark:="is Bad";
            ELSE remark:="big Problem";
       END CASE;
END;

```

#### 循环控制语句

##### loop循环

> **LOOP**
>      **statements;**
> **END LOOP;**

```plsql
DECLARE
    v_count integer := 1;
BEGIN
    LOOP
        v_count:=v_count+1;
        IF v_count>=10 THEN
            EXIT;
        END IF;
    END LOOP;
END;
```

书写loop循环时记得书写跳出的exit语句，否则会造成死循环。

##### while-loop

类似于Java的while循环

> **WHILE…  LOOP**
>      **statements;**
> **END LOOP;**

```plsql
declare
i number(10) := 1;
begin
 while i<=10 loop
    dbms_output.put_line(i);
    i:=i+1;
    end loop;
end;

```

##### for-loop循环

类似于for循环

> **FOR loop_count IN [REVERSE] lower_bound..height_bound LOOP**
>       **statements;**
> **END LOOP;**
>
> loop_count--循环变量；lower_bound:循环最小次数；heigh_bound:循环次数最大值

```plsql
begin
  for i in 21..30
  loop
    dbms_output.put_line(i);
  end loop;
end;
```

显示游标如果使用for循环遍历，会自动开启和关闭游标。

#### 游标

用来处理使用select语句从数据库中检索到的多行记录的工具

游标的分类

- 显示游标
  - 返回多条记录时，使用显示游标逐行读取
- 隐式游标
  - PL/SQL自动为DML语句创建隐式游标，包含一条返回记录

| **属性名称**  | **说 明**                                                    |
| ------------- | ------------------------------------------------------------ |
| %found****    | **用于检验游标是否成功，通常在FETCH语句前使用，当游标按照条件查询出一条记录时，返回true** |
| **%isopen**   | **判断游标是否处于打开状态，视图打开一个已经打开或者已经关闭的游标，将会出现错误** |
| **%notfound** | **与%found的作用相反，当按照条件无法查询到记录时，返回true** |
| **%rowcount** | **循环执行游标读取数据时，返回检索出的记录数据的行数**       |

##### 游标的声明：

```plsql
CURSOR cursor_name [ ( parameter [ , parameter]……)]
[ RETURN return_type ] IS selectsql
```

CURSOR：用于声明一个游标
parameter：可选参数，用于指定参数类型、模式等
return：可选，指定游标的返回类型
selectsql:需要处理的select语句，不能含INTO子句

##### 打开游标

```plsql
open cursor_name
```

使用open语句开启一个游标

##### 提取游标

```plsql
fetch cursor_name into variable_list
```

使用fetch语句实现对游标内容的读取

variable_list必须与从游标提取的结果集类型相同

##### 关闭游标

```plsql
close cursor_name
```

使用close语句关闭一个游标

关闭游标后，所有资源都将被释放，且不能再次被打开。

```plsql
DECLARE
     fname varchar2(20);
     lname varchar2(20);
     --声明一个游标
     CURSOR c_student is select firstname, lastname from students where id=1001 ;
BEGIN
     --打开游标
    OPEN c_student;
    - - 判断游标是否返回记录
    if c_student%NOTFOUND THEN
           dbms_output.put_line('没有找到相应的记录');
    else
    --从游标中读取记录
          fetch c_student into fname,lname;
          dbms_output.put_line(fname||''||lname);
    end if;
   CLOSE c_student;
END;

```

隐式游标的声明与使用

zaiPL/SQL块中的DML语句会自动创关键字指代游标建隐式游标，使用sql关键字指代游标。

```plsql
--隐式游标
declare
begin
  delete from student where sname = '';
  dbms_output.put_line(sql%rowcount);
end;
--对隐式游标而言其他属性基本没什么意义，唯一有用的就是rowcount
```

minus关键字去同存异

### 视图

- Oracle创建视图的语法非常重要，因为Oracle创建视图使我们最常用的操作之一
- 视图是基于一个表或多个表或视图的逻辑表，本身不包含数据，通过它可以对表里面的数据进行查询和修改。视图基于的表称为基表。（试图一般只用来查询）
- 视图是存储在数据字典里的一条select语句。 通过Oracle创建视图可以提取数据的逻辑上的集合或组合

```plsql
--视图创建的语法
CREATE [OR REPLACE] [FORCE|NOFORCE] VIEW view_name
[(alias[, alias]...)]   
AS subquery  
[WITH CHECK OPTION [CONSTRAINT constraint]]  
[WITH READ ONLY]
--OR REPLACE    ：若所创建的试图已经存在，ORACLE自动重建该视图；
--FORCE  ：不管基表是否存在ORACLE都会自动创建该视图；
--NOFORCE   ：只有基表都存在ORACLE才会创建该视图：
--alias ：为视图产生的列定义的别名；
--subquery     ：一条完整的SELECT语句，可以在该语句中定义别名；
--WITH CHECK  OPTION ：插入或修改的数据行必须满足视图定义的约束；
--WITH READ ONLY ：该视图上不能进行任何DML操作。
```

#### 视图的优点

1. 对数据库的访问，因为视图可以有选择性的选取数据库里的一部分。
2. 用户通过简单的查询可以从复杂查询中得到结果。
3. 维护数据的独立性，试图可从多个表检索数据。
4. 对于相同的数据可产生不同的视图。

试图分为简单视图和复杂视图（通俗的讲简单视图时单表，复杂视图是多表）

### 过程

过程：将SQL或者PL/SQL代码块集中用于完成特定功能的集合

#### **过程结构**

- 声明部分：包括类型、变量、游标
- 执行部分：完成功能而编写的SQL语句或则是PL/SQL代码块
- 异常处理部分

```plsql
CREATE [ OR REPLACE] PROCEDURE procedure_name  --创建过程
[ ( parameter1 [ { in | out | in out} param1_type  parameter2 [ { in | out | in out} param2_type
……
parameterN [ { in | out | in out} paramN_type]]   --可选参数
{is | as}
begin  --执行的步骤、过程的具体实现
                
end;--结束
                
in--传入的值  
out--传出的值
```

注意：

- 创建过程不使用DECLARE关键字
- 在创建过程时可指定参数

#### 过程的调用与删除

```plsql
--调用带参过程
begin 
过程名(参数)
end;

--调用无参过程
begin
过程名
end;

--删除过程
drop procedure 过程名
```

过程的大致用法与Java的方法类似

### 函数

函数：与过程类似，是一组SQL语句或者PL/SQL语句块的集合，同时能够返回执行结果。

```plsql
--创建函数
CREATE [ OR REPLACE] FUNCTION function_name
[ ( parameter1 [ { IN | OUT | IN OUT} param1_type
parameter2 [ { IN | OUT | IN OUT} param2_type
……
parameterN [ { IN | OUT | IN OUT} paramN_type]]
RETURN returntype { IS | AS }
function _body;
```

- 创建函数不使用DECLARE关键字
- 在创建函数时可指定参数

```plsql
create or replace function fun_name(参数1，参数2)
return returnType as 变量名 returnType
变量声明部分
begin
end;
/*Example:
create or replace function now--如果没有参数可以不写括号
return varchar2 as nowtime varchar2(50)
begin
nowtime := to_char(sysdate,'yyyy-mm-dd hh24:mi:ss');
return nowtime;
end;
*/
```

#### 函数的结构

- 声明部分：包括类型、变量、游标
- 执行部分：完成功能而编写的SQL语句或则是PL/SQL代码块
- 异常处理部分

函数的结构与过程的结构大体相同。

函数体内允许有多个return
执行return语句，函数将执行结束并返回结果

#### 函数的调用与删除

```plsql
--调用函数--
DECLARE
--声明变量接收函数的返回值
     v_count number;
BEGIN
    v_count:=GETCOUNT('MUSIC');
    Dbms_Output.put_line(v_count);
END;

--删除函数
DROP FUNCTION 函数名
```

| ** **        | **过程**                 | **函数**                     |
| ------------ | ------------------------ | ---------------------------- |
| **标识符**   | **PROCEDURE**            | **FUNCTION**                 |
| **返回值**   | **必须使用变量形参**     | **用函数名直接返回**         |
| **赋值**     | **不能赋值并定义类型**   | **可以定义类型，并直接赋值** |
| **调用方式** | **独立的过程调用句**     | **以表达式方式调用**         |
| **目的**     | **完成一系列的数据处理** | **获得函数返回值**           |

### 创建表空间用户及其他

创建表空间

```plsql
create tablespace space_name datafile '路径名' size (空间大小例如：500M)
```

创建用户

```plsql
create user user_name identified by  User_password default tablespace space_name
```

授权

```plsql
grant (权限名例如： connect,resource,dba) to user_name
```

收回权限

```plsql
revoke (权限名例如： resource,dba) from user_name
```

### **序列**

序列(SEQUENCE)是序列号生成器，可以为表中的行自动生成序列号，产生一组等间隔的数值(类型为数字)。不占用磁盘空间，占用内存。

主要用途是生成表的主键值，可以在插入语句中引用，也可以通过查询检查当前值，或使序列增至下一个值。

```plsql
	CREATE SEQUENCE 序列名

　　[INCREMENT BY n] --定义序列的步长，如果省略默认为1如果出现负值，则代表Oracle序列的值是按照此步长递减的。
　　[START WITH n] --产生的第一个值，默认为1
　　[{MAXVALUE/ MINVALUE n| NOMAXVALUE}] --定义序列生成器产生的最大值 nomaxvalue是默认选项代表没有最大值定义
　　（对于递增Oracle序列，系统能够产生的最大值是10的27次方;对于递减序列，最大值是-1。
　　对于递减序列，系统能够产生的最小值是?10的26次方;对于递增序列，最小值是1。）
　　[{CYCLE|NOCYCLE}] --表示当序列生成器的值达到先之后是否循环，cycle代表循环，nocycle代表不循环。
　　（如果循环，则当递增序列达到最大值时，循环到最小值;对于递减序列达到最小值时，循环到最大值。如果不循环，达到限制值后，继续产生新值就会发生错误。）
　　[{CACHE n| NOCACHE}]; --定义存放序列的内存块的大小默认为，20。nocache表示不对序列进行内存缓冲。
　　（对序列进行内存缓冲，可以改善序列的性能。）
```

```plsql
/*Example：
create sequence SEQ_GRADE
minvalue 11
maxvalue 9999999999999999999999999
start with 11
increment by 1
cache 20;
*/
```



### 创建触发器

```plsql
CREATE [ OR REPLACE] trigger 触发器名 触发时间 触发事件 
on 表名
[FOR EACH ROW]
BEGIN
pl/sql语句
END;

```

**触发器**:触发器是一种特殊的过程，但是用户不能直接调用触发器。触发器是当特定事件出现时自动执行的代码块。（使用触发器可以大大增强Oracle的默认功能，进而提供高度可定制的数据库。用户不会接收到Oracle正在执行触发器的指示，除非触发器导致了开发人员不能正确处理的错误.）

**触发器的类型**

Oracle系统有5种类型的触发器。每一种类型的触发器都可以完成不同的任务。这5种类型的触发器分别是：**语句触发器**、**行触发器**、**instead of触发器**、系**统事件触发器**和**用户事件触发器**

#### 语句触发器

语句触发器是在表上或某些视图上执行的特定语句的触发器。语句触发器能够与insert、update或delete语句或这些语句的任意组合关联。用户既可以在表的insert或update语句上使用单独的触发器，也可以在表的insert和update语句的组合上使用触发器，甚至可以在单独的表上拥有多个insert语句触发器。

```plsql
--创建语句触发器
CREATE OR REPLACE Trigger statementtri
before insert or update or delete --执行触发器的时机
on tablename --执行触发器的表
BEGIN
 dbms_output.put_line('trigger execute!');
END;
```

#### 行触发器

行触发器的定义方式与语句触发器类似但还是有两个例外的。

行触发器要在触发器定义的触发语句中包含for each row子句 
在after(before)…for each row触发器中，可以引用受到影响的行值，甚至可以在触发器中设置这些值。

```plsql
--创建触发器
CREATE OR REPLACE TRIGGER 触发器名
after insert --执行触发器的时机
on 表名  --执行触发器的表
for each row --表示是个行触发器
begin 
--触发器的具体执行的实现
end;
```

### 事务

事务：一次不可分割的操作，称之为一个事务。（未提交前算作同一次事务）

事务是应用程序中一系列严密的操作，所有操作必须成功完成，否则在每个操作中所作的所有更改都会被撤消。也就是事务具有原子性，一个事务中的一系列的操作要么全部成功，要么一个都不做。

#### 事务的四大特性

**数据库事务 transanction 正确执行的四个基本要素。ACID,原子性(Atomicity)、一致性(Correspondence)、隔离
性(Isolation)、持久性(Durability)。**

- **原子性**：整个事务中的所有操作，要么全部完成，要么全部不完成，不可能停滞在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。
- **一致性**：在事务开始之前和事务结束以后，数据库的完整性约束没有被破坏。
- **隔离性**：隔离状态执行事务，使它们好像是系统在给定时间内执行的唯一操作。如果有两个事务，运行在相同的时间内，执行 相同的功能，事务的隔离性将确保每一事务在系统中认为只有该事务在使用系统。这种属性有时称为串行化，为了防止事务操作间的混淆，  必须串行化或序列化请 求，使得在同一时间仅有一个请求用于同一数据。
- **持久性**：在事务完成以后，该事务所对数据库所作的更改便持久的保存在数据库之中，并不会被回滚。

## JDBC

概念：Java DateBase Connectivity    Java数据库连接，Java语言操作数据库

这个jar包就是具体的实现类。

JDBC本质：其实是官方定义的一套操作所有关系型数据库的规则，即接口。各个数据库厂商去实现这套接口，提供数据库驱动jar包，我们可以使用这套接口（JDBC）编程，真正执行的代码是驱动jar包中的实现类。

![](F:\md笔记文件\javaimg\JDBC工作原理.png)

### 快速入门

步骤：

1. 导入驱动jar包

   1. 复制jar包文件到新建的lib文件夹下
   2. 右键 Add path添加到文件中使用的操作步骤

2. 注册驱动

   ```java
   class.forName(“完整类名”);
   ```

3. 获取数据库连接对象 Connection

   ```java
   Connection conn = DriverManager.getConnection("url","用户名","密码");
   ```

4. 定义sql语句

   ```java
   String sql = "update student set studentname = '张三' where studentno = 101"；
   ```

5. 获取执行sql语句的对象 statement

   ```java
   Statement stmt = conn.createStatement();
   ```

6. 执行sql，接受返回结果

   ```java
   int count = stmt.executeUpdate(sql);
   ```

7. 处理结果

   ```java
   system.out.println(count)
   ```

8. 释放资源

   ```java
   stmt.close();
   conn.close();
   ```

### 详解各个对象

![](F:\md笔记文件\javaimg\JDBCapi.png)

- DriverManager：驱动管理对象

  功能：

  1. 注册驱动：告诉程序应该用哪一个接口来驱动jar包

     ```java
     static void registerDriver(Driver driver):注册与给定的驱动程序 Driver Manager。
     class.forName("jdbc类名")
     ```

     jar包中都有静态代码块来实现驱动注册步骤。

  2. 获取数据库连接

     ```java
     static Connection getConnection(String url,String user,String password)
         //url:指定连接的路径
         //user:用户名
         //password：密码
     ```

- Connection：数据库连接对象

  功能：

  1. 获取执行sql对象

     ```java
     *statement createStatement()
     PreparedStatement *perpareStatement(String sql)
     ```

  2. 管理事务

     - 开始事务：

       ```java
       void setAuto Commit(boolean autoCommit)//调用该方法设置参数为false，即开启事务
       ```

     - 提交事务

       ```java
       void commit()
       ```

     - 回滚事务

       ```java
       void rollback()
       ```

- Statement：执行sql的对象

  执行sql：

  1. ```java
     boolean  execute(String sql)//可以执行任意的sql了解
     ```

  2. ```java
     int executeUpdate(String sql)//执行DML（update,delete,insert）、DDL(create,alter,drop)语句
     ```

     

- ResultSet：结果集对象

- PreparedStatement：执行sql的对象

### JDBC驱动

JDBC驱动由数据库厂商提供

- 在个人开发与测试中，可以使用JDBC-ODBC桥连方式
- 在生产型开发中，推荐使用纯Java驱动方式

![](F:\md笔记文件\javaimg\JDBC驱动.png)

**使用JDBC-ODBC桥方式连接数据库**：

- 将对JDBC API的调用，转换为对另一组数据库连接API的调用
- 优点：可以访问所有ODBC可以访问的数据库
- 缺点：执行效率低、功能不够强大

**使用纯Java方式连接数据库** ：

- 由JDBC驱动直接访问数据库
- 优点：100% Java，快又可跨平台
- 缺点：访问不同的数据库需要下载专用的JDBC驱动

注意：当你在数据库操作时，未结束一次事务的话，直接使用JDBC_Java来进行数据库的一系列操作的话，程序会卡死。这是事务的隔离性的直接表现。

注意：Java里用的date类都是util的date包。

执行sql语句时：增删改用executeUpdate(sql)方法，查询用executeQuery(sql)

#### Statement常用方法

| 方法名                             | 说  明                                                       |
| ---------------------------------- | ------------------------------------------------------------ |
| ResultSet executeQuery(String sql) | 执行SQL查询并获取到ResultSet对象                             |
| int executeUpdate(String sql)      | 可以执行插入、删除、更新等操作，返回值是执行该操作所影响的行数 |
| boolean execute(String sql)        | 可以执行任意SQL语句，然后获得一个布尔值，表示是否返回ResultSet |

#### ResultSet常用方法

| 方法名                            | 说  明                                  |
| --------------------------------- | --------------------------------------- |
| boolean next()                    | 将光标从当前位置向下移动一行            |
| boolean previous()                | 游标从当前位置向上移动一行              |
| void close()                      | 关闭ResultSet 对象                      |
| int getInt(int colIndex)          | 以int形式获取结果集当前行指定列号值     |
| int getInt(String colLabel)       | 以int形式获取结果集当前行指定列名值     |
| float getFloat(int colIndex)      | 以float形式获取结果集当前行指定列号值   |
| float getFloat(String colLabel)   | 以float形式获取结果集当前行指定列名值   |
| String getString(int colIndex)    | 以String 形式获取结果集当前行指定列号值 |
| String getString(String colLabel) | 以String形式获取结果集当前行指定列名值  |

通用的JDBCUtil，需要配合着资源文件使用。

```java
package com.rentCar.Util;

import java.lang.reflect.Field;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.ArrayList;
import java.util.ResourceBundle;

import com.rentCar.Common.entry.Car;
import com.rentCar.Common.entry.Record;
import com.rentCar.User.entry.User;


public class JDBCUtil {
	private static String driver; // 驱动名
	private static String url;
	private static String user;
	private static String password;
	private Connection conn = null;
	private PreparedStatement state = null;
	private ResultSet rs = null;
	// 加载驱动等事前准备工作
	static {
		try {
			ResourceBundle bundle = ResourceBundle.getBundle("jdbc");
			driver = bundle.getString("driver");
			url = bundle.getString("url");
			user = bundle.getString("user");
			password = bundle.getString("password");
			Class.forName(driver);
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		}
	}

	// 获取驱动连接
	public static Connection getConnection() {
		Connection conn = null;
		try {
			conn = DriverManager.getConnection(url, user, password);
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return conn;
	}

	/**
	 * 返回查询到的数据集合以ArrayList集合传出。
	 */
	public static <T> ArrayList<T> Select(ResultSet rs, Class<T> clazz) {
		ArrayList<T> arr = new ArrayList<T>();
		Field[] fields = clazz.getDeclaredFields();
		try {
			// 指向查询的结果集的每一行属性
			while (rs.next()) {
				// 创建一个对象接受属性信息
				T nowUser = clazz.newInstance();
				for (Field field : fields) {
					field.setAccessible(true);// 可读取私有属性
					// getObject()：获取当前行的指定列的值。field.getName()获取当前属性的指定列名称
					// 将每个字段的值传入nowUser对象中
					ResultSetMetaData metaData = rs.getMetaData();
					for (int i = 1; i <= metaData.getColumnCount(); i++) {
						String columnName = metaData.getColumnName(i);
						if (columnName.toLowerCase().equals(field.getName().toLowerCase())) {
							field.set(nowUser, rs.getObject(field.getName()));
						}
					}
				}
				// 在集合中添加nowUser对象。
				arr.add(nowUser);
			}
		} catch (SQLException e) {
			e.printStackTrace();
		} catch (InstantiationException e) {
			e.printStackTrace();
		} catch (IllegalAccessException e) {
			e.printStackTrace();
		}
		return arr;
	}

	/**
	 * 根据需求查询汽车信息
	 * 
	 * @param sql
	 *            需求的sql语句
	 * @return 返回一个需要查询到的汽车信息
	 */
	public ArrayList<Car> selectCar(String sql) {
		ArrayList<Car> arr = new ArrayList<Car>();
		try {
			conn = JDBCUtil.getConnection();
			state = conn.prepareStatement(sql);
			rs = state.executeQuery();
			arr = JDBCUtil.Select(rs, Car.class);
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			JDBCUtil.close(rs, state, conn);
		}
		return arr;
	}

	/**
	 * 根据需求修改/添加信息记录
	 * 
	 * @param sql
	 *            需求的sql语句
	 * @return 返回一个是否修改成功的信息
	 */
	public boolean UpdateNothing(String sql) {
		try {
			conn = JDBCUtil.getConnection();
			state = conn.prepareStatement(sql);
			state.executeUpdate();
		} catch (SQLException e) {
			e.printStackTrace();
			return false;
		} finally {
			JDBCUtil.close(rs, state, conn);
		}
		return true;
	}

	/**
	 * 根据需求查询租赁记录
	 * 
	 * @param sql
	 *            查询筛选租赁记录的sql语句
	 * @return 返回一个需求的的租赁记录
	 */
	public ArrayList<Record> selectRecord(String sql) {
		ArrayList<Record> arr = new ArrayList<Record>();
		try {
			conn = JDBCUtil.getConnection();
			state = conn.prepareStatement(sql);
			rs = state.executeQuery();
			arr = JDBCUtil.Select(rs, Record.class);
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			JDBCUtil.close(rs, state, conn);
		}
		return arr;
	}

	/**
	 * 查找用户信息的方法
	 * 
	 * @param sql
	 *            通过sql语句来指定获取谁的信息或者哪一批的信息
	 * @return 返回一个装载了指定查找的所有用户的集合
	 */
	public ArrayList<User> selectUser(String sql) {
		ArrayList<User> arr = new ArrayList<User>();
		try {
			conn = JDBCUtil.getConnection();
			state = conn.prepareStatement(sql);
			rs = state.executeQuery();
			arr = JDBCUtil.Select(rs, User.class);
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			JDBCUtil.close(rs, state, conn);
		}
		return arr;
	}
	// 关闭资源
	public static void close(ResultSet rs, Statement state, Connection conn) {
		// 先try再if的原因是如果一开始就if的话直接判断为false的话
		// 就会直接跳出语句，不执行接下来的步骤，所以一定要先try再用if判断是否为空，决定要不要关闭
		// 最后嵌套的关闭资源必须放在finally语句块里面，因为不管程序报不报错，这句话都会执行
		// 保证了第一个资源报错也不会影响之后的资源关闭。
		try {
			if (rs != null) {
				rs.close();
			}
		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			try {
				if (state != null) {
					state.close();
				}
			} catch (SQLException e) {
				e.printStackTrace();
			} finally {
				try {
					if (conn != null) {
						conn.close();
					}
				} catch (SQLException e) {
					e.printStackTrace();
				} finally {

				}
			}
		}
	}

}

```



## MVC分层

Dao层，Sever层，Control层，View层，Entry实体类包