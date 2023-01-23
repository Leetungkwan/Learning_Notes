# 约束

## 概念：约束是作用于表中字段上的规则，用于限制存储在表中的数据。

## 目的：保证数据库中数据的正确、有效性和完整性。

| 约束                     | 描述                                                     | 关键字      |
| ------------------------ | -------------------------------------------------------- | ----------- |
| 非空约束                 | 限制该字段的数据不能为null                               | not null    |
| 唯一约束                 | 保证该字段的所有数据都是唯一、不重复的                   | unique      |
| 主键约束(序号)           | 主键是一行数据的唯一标识，要求非空且唯一                 | primary key |
| 默认约束                 | 保存数据时，如果未指定该字段的值，则采用默认值           | default     |
| 检查约束(8.0.16版本之后) | 保证字段值满足某一个条件                                 | check       |
| **外键约束**             | 用来让两张表的数据之间建立连接，保证数据的一致性和完整性 | foreign key |

## 外键约束

1. `alter table 表名 add constraint 外键名称 foreign key referens(外键字段名) 主表(主表列名);` 添加外键

   实际语句：`alter table emp add constraint  foreign_emp_id foreign key(dept_id)  references dept(id);`

2. `alter table 表名 drop foreign key 外键名称;` 删除外键

   实际语句：`alter table emp drop foreign key foreign_emp_id;`

### 删除/更新行为

| 行为        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| no action   | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则不允许删除/更新。 (与 RESTRICT 一致) 默认行为 |
| restrict    | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则不允许删除/更新。 (与 NO ACTION 一致) 默认行为 |
| cascade     | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有，则也删除/更新外键在子表中的记录。 |
| set null    | 当在父表中删除对应记录时，首先检查该记录是否有对应外键，如果有则设置子表中该外键值为null（这就要求该外键允许取null）。 |
| set default | 父表有变更时，子表将外键列设置成一个默认的值 (Innodb不支持)  |

语法：`alter table 表名 add constraint 外键名称 foreign key referens(外键字段名) 主表(主表列名); on update 行为 on delete 行为;`















