# SQL错误异常

**ORA-00918**: column ambiguously defined

> 未明确定义列，select 查询的字段在from的两张表中都存在， 导致数据库无法区别需要查询的字段来自于哪张表。**需要在列名前添加表名**。

**ORA-00904**: "表名"."列名": invalid identifier

> 当重命名表名后，使用的**表名必须是重命名的名字**。

**ORA-00979**: not a GROUP BY expression

> 输出的字段没有通过group by进行分组的字段。

**ORA-00936**: missing expression

> 缺失表达式

**ORA-01427**: single-row subquery returns more than one row

> 数据库按照你的条件查询有多个重复的数据。 
>
> 部分修改方式：将=修改为in

**ORA-00907**: missing right parenthesis

缺失右侧括号

**ORA-00971**: missing SET keyword

> 缺少set关键字

**ORA-00917**: missing comma

> 缺少逗号

