# DDL语句是Data Definition Language
## 数据定义语言，用来定义数据库对象(数据库，表，字段)

>>要求掌握基本的语句用法，但在后面使用DataGrip之后可以直接使用GUI页面进行创建，减少掌握量；重点是数据类型（因为没学过Java语言）
### 数据库操作

1. `show databases;` 查询所有数据库
2.  `create database [if not exists] 数据库名;` 创建数据库,[ ]里面的内容基本用不上
3. `select database();` 查询当前数据库
4.  `drop database [if exists] 数据库名;` 删除数据库
5. `use 数据库名;` 

### 表操作

1. `show tabels;` 查询当前数据库的所有表
2. create table 表名(
		字段1 字段1类型 [ COMMENT 字段1注释 ],
		字段2 字段2类型 [COMMENT 字段2注释 ],
		字段3 字段3类型 [COMMENT 字段3注释 ],
		字段n 字段n类型 [COMMENT 字段n注释 ]
	) [ COMMENT 表注释 ] ; 创建表结构
3. 数据类型： 数值类型、字符串类型、日期时间类型
	1. 数值类型（常用）：tinyint（1byte）；有signed和unsigned范围
	2. 字符串类型（常用）： char(0-255bytes)， 定长字符串； varchar(0-655535bytes)，变长字符串。
	3. 日期时间类型（常用）： date（3），范围：1000-01-01至9999-12-31
4. 表修改
	1. `alter table 表名 add 字段名 类型（长度）[comment ];` 添加字段
	2. `alter table 表名 modify 字段名 新数据类型（长度）;`修改数据类型
	3. `alter table 表名 change 旧字段名 新字段名 类型（长度）[comment ];` 修改字段名和数据类型
	4. `alter table 表名 drop 字段名;` 删除字段
	5. `alter table 表名 rename to 新表名; ` 修改表名
	6. `drop table [if exists] 表名;` 删除表
	7. `truncate table 表名;` 删除指定表并重新创建表