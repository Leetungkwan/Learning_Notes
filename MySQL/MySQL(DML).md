# DML全称是Data Manipulation Language（数据操作语言），用来对数据库中表的数据记录进行增、删、改操作

## 添加数据

1. `insert into 表名（字段1，字段2，。。。） values（值1，值2，。。。）;` 给指定字段添加数据

   实际语句：`insert into tb_user(id, name, age, gender) values (2022, 'pi', 18, 'm');`

2. `insert into 表名 values（值1，值2，。。。）;` 给全部字段添加数据

   实际语句：`insert into tb_user values (2, 'bob', 28, 'm');`

3. `insert into 表名（字段1，字段2，。。。） values（值1，值2，。。。）, values（值1，值2，。。。）, values（值1，值2，。。。）;` 批量给指定字段添加数据

   `insert into 表名 values（值1，值2，。。。）, （值1，值2，。。。）, （值1，值2，。。。）;` 批量给全部字段添加数据

   实际语句：`insert into tb_user(id, name, age, gender) values (3, 'peter', 38, 'n'), (4, 'park', 48, 'n');`

## 修改数据

1. `update 表名 set 字段名1 = 值1 , 字段名2 = 值2 , .... [ where 条件 ] ;` 若无where，则对整个表进行操作。

   实际语句：`update tb_user set age = 58 where name = 'pi';`

## 删除语句

1. `delete from 表名 [ where 条件 ] ;` 若无where，则对整个表进行操作。

   实际语句：`delete from tb_user where id = 2022;`

   