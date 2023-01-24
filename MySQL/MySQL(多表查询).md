## 类型

- **一对多** 实现：在多的一方建立外键，指向一的一方的主键
- **多对多** 实现：建立第三张中间表，中间表至少包含两个外键，分别关联两方主键
- **一对一** 实现：在任意一方加入外键，关联另外一方的主键，并且设置外键为唯一的(UNIQUE)



### 内连接：相当于查询A、B交集部分数据

1. `select 字段列表 from 表1，表2 where 条件..;` 隐式连接

   实际语句：`select emp.name, dept.name from emp, dept where emp.dept_id = dept.id;`

2. `select 字段列表 from 表1 [inner] join 表2 on 连接条件..;` 显式连接（用得比较多）

   实际语句：`select e.name, d.name from emp e join dept d on e.dept_id = d.id;`

   

### 外连接

左外连接相当于查询表1(左表)的所有数据，当然也包含表1和表2交集部分的数据。（记一个就行了）

语法：`select 字段列表 from 表1 left [outer] join 表2 on 条件...;` 

实际语句：*select * from emp e left join dept d on d.id = e.dept_id;``

### 自连接查询

自连接查询，顾名思义，就是自己连接自己，也就是把一张表连接查询多次（把一个表看成两个表）

语法：`select 字段列表 from 表A 别名A join 表B 别名B on 条件...`

实际语句：`select a.name, b.name from emp a join emp b on a.managerid = b.id;`

### 联合查询

对于union查询，就是把多次查询的结果合并起来，形成一个新的查询结果集

语法：

```sql
select 字段列表 from 表A ...
union [all]
select 字段列表 from 表B...;
```



## 子查询

### 分类

- 标量子查询（子查询结果为单个值）
-  列子查询(子查询结果为一列)
-  行子查询(子查询结果为一行)
-  表子查询(子查询结果为多行多列)

### 语法：与查询无区别，只不过多了嵌套

### 标量子查询

常用的操作符：= <> > >= < <= 

### 列子查询

常用的操作符：in 、not in 、 any 、some 、 all

| 操作符      | 描述                                 |
| ----------- | ------------------------------------ |
| in          | 在指定的集合范围之内，多选一         |
| not in      | 不在指定的集合范围之内               |
| any（some） | 子查询返回列表中，有任意一个满足即可 |
| all         | 子查询返回列表的所有值都必须满足     |

### 行子查询

常用的操作符：= 、<> 、IN 、NOT IN

### 表子查询

常用的操作符：IN 



