# DCL英文全称是Data Control Language(数据控制语言)，用来管理数据库用户、控制数据库的访问权限

## 管理用户

1. `create user '用户名'@'主机名' identified by '密码';` 创建用户

   实际语句：`create user 'test2'@'%' identified by '123456';`

2. `alter user '用户名'@'主机名' identified with mysql_native_password by '新密码'; ` 修改用户密码

   实际语句：`alter user 'test2'@'%' identified with mysql_native_password by '1234';` 

3. `drop user '用户名'@'主机名'; ` 

   实际语句：``

   ```
   drop user 'test1'@'localhost' ;
   drop user 'test2'@'%' ;
   ```

## 权限控制

1. `show grants for '用户名'@'主机名';` 查询权限

   实际语句：`show grants for 'test1'@'localhost';`

2. `grant 权限列表 on 数据库名.表名 to '用户名'@'主机名';` 授予权限

   实际语句：`grant all on mysql.user to 'test1'@'localhost';`

3. `revoke 权限列表 on 数据库名。表名 from '用户名'@'主机名';` 撤销权限

   实际语句：``









