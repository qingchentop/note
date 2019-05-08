Linux用户管理

```shell
#查看用户
id
uid=0(root) gid=0(root) 组=0(root) 环境=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023

#查看root用户
uid=0(root) gid=0(root) 组=0(root)

#添加一个用户: useradd 用户名
#注意：创建一个用户的同时会创建一个组，当前创建的用户加入这个组。
useradd user1

#删除一个用户： userdel -r 用户名
userdel -r user1

#设置用户密码: passwd 用户名 。再跟进提示输入密码
passwd user1
更改用户 user1 的密码 。
新的 密码：




```

创建删除用户更新的配置文件

```shell
#添加用户
useradd user1

#文件1：“/etc/passwd”,存储用户信息
user1:x:1000:1000::/home/user1:/bin/bash
#文件2：“/etc/shadow”,存储用户密码
user1:!!:18024:0:99999:7:::
#文件3：在“/home”目录下生成用户目录
/home/user1
#注：root用户“家”目录在“/”目录下。普通用户的“家”目录在“/home”下


```

用户与组

```shell
#把用户加入组：“gpasswd -a 用户名 组名”
gpasswd -a user1 root
正在将用户“user1”加入到“root”组中

#把用户移出组: "gpasswd -d 用户名 组名"
gpasswd -d user1 root
正在将用户“user1”从“root”组中删除



```

