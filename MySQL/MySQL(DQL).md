# DQL英文全称是Data Query Language(数据**查询**语言)，数据查询语言，用来查询数据库中表的记录。

## 基本查询

1. `select 字段1, 字段2, 字段3 ... from 表名 ;` 查询多个字段

   实际语句：`select name,workno,age from emp;`

2. `select 字段1 [as 别名], 字段2 [as 别名], 字段3 [as 别名] ... from 表名` 查询多个字段（起别名）

   实际语句：`select workaddress as '工作地址' from emp;`

3. `select distinct 字段1, 字段2, 字段3 ... from 表名` 去除重复的数据

   实际语句：`select distinct workaddress from emp;` 

   

## 条件查询

1. `select 字段列表 from 表名 where 条件列表`

   实际语句：`select * from emp where age=88`

   注意几个特殊用法 between...and..(在某个范围内，包含边界值)，in(...)(在in之后的列表中的值，多选一)，like(_匹配单个字符，%匹配任意个字符)，is null(是null)

   

## 聚合函数

定义：将一列数据作为一个整体，进行纵向计算

1. `select 聚合函数(字段列表) from 表名;`

   实际语句：`select count(id) from emp;`

   常见函数：count（统计数量），max（最大值），min（最小值），avg（平均值），sum（求和）

   

## 分组查询

`select 字段列表 from 表名 [where 条件] group by 分组字段名 [having 分组后过滤条件]`

### 注意事项

1. where 和having区别
   - 执行时机不同：where是分组之前进行过滤，不满足where条件，不参与分组；而having是分组
     之后对结果进行过滤。
   - 判断条件不同：where不能对聚合函数进行判断，而having可以。

2. 分组之后，查询的字段一般为聚合函数和分组字段，查询其他字段无任何意义。即select后面的字段名和group by后面的字段名一样，查询出的字段名才有意义

   

实际语句：`select workaddress, count(id) from emp where age<45 group by workaddress having count(id)>=3;`

## 排序查询

`select 字段列表 from 表名 order by 字段1 排序类型（asc，desc），字段2 排序类型（asc，desc）`

**当字段1相同时才会采取字段2排序**

实际语句：`select * from emp order by age asc, entrydate desc;`

## 分页查询

`select 字段列表 from 表名 limit 起始索引，查询记录数;`

### 注意事项

- 起始索引从0开始，起始索引 = （查询页码 - 1）* 每页显示记录数。
-  分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT。
-  如果查询的是第一页数据，起始索引可以省略，直接简写为 limit 10。 

实际语句：`select * from emp limit 10,10;`

















