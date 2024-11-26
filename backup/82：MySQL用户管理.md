# 82：MySQL用户管理

* <span data-type="text" style="background-color: var(--b3-card-warning-background); color: var(--b3-card-warning-color);">输入（问题）</span>：MySQL用户管理？

  * <span data-type="text" style="background-color: var(--b3-card-info-background); color: var(--b3-card-info-color);">例子</span>：无

  * <span data-type="text" style="background-color: var(--b3-card-error-background); color: var(--b3-card-error-color);">输出（答案）</span>：<span data-type="text" style="background-color: var(--b3-card-success-background); color: var(--b3-card-success-color);">知识描述</span>：MySQL用户管理：MySQL 是一个多用户的数据库系统，按权限，用户可以分为两种：root 用户，超级管理员，和由 root 用户创建的普通用户。

  * <span data-type="text" style="background-color: var(--b3-card-error-background); color: var(--b3-card-error-color);">输出（答案）</span>：<span data-type="text" style="background-color: var(--b3-card-success-background); color: var(--b3-card-success-color);">知识描述</span>：用户管理：  
    创建用户：`CREATE USER username IDENTIFIED BY 'password';`​

    查看用户：`SELECT USER,HOST FROM mysql.user;`​

    删除用户：`DROP USER username@localhost;`​

    示例：创建一个 u_sxt 的用户，并查看创建是否成功。  
    ​`create user u_sxt IDENTIFIED by 'sxt';
    select user,host from mysql.user;`​

    示例：删除 u_sxt 用户。  
    ​`drop user 'u_sxt'@'localhost';`​

  * <span data-type="text" style="background-color: var(--b3-card-error-background); color: var(--b3-card-error-color);">输出（答案）</span>：<span data-type="text" style="background-color: var(--b3-card-success-background); color: var(--b3-card-success-color);">知识描述</span>：权限管理：新用户创建完后是无法登陆的，需要分配权限。

    语法：`GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY 'password'`​相当于`GRANT 权限列表 ON 数据库.表 TO 用户名@登录主机 IDENTIFIED BY "密码"`​

    权限列表：  
    
![image-20241126223604-bpestqz](https://github.com/user-attachments/assets/b81e0f0d-b5f8-498f-8cd4-490dd8a725ea)

   
![image-20241126223631-69cgm9h](https://github.com/user-attachments/assets/985c17cc-a988-4594-9023-3a1c2bc587f9)


    示例：为 u_sxt 用户分配只能查询 bjsxt 库中的 emp 表，并且只能在本机登陆的权限。  
    ​`grant select ON bjsxt.emp to 'u_sxt'@'localhost' IDENTIFIED by 'sxt';`​

    **刷新权限**：每当调整权限后，通常需要执行以下语句刷新权限。`FLUSH PRIVILEGES;`​

---

　　<span data-type="text" style="background-color: var(--b3-card-success-background); color: var(--b3-card-success-color);">日期：2024年11月26日 22点38分</span>

　　‍