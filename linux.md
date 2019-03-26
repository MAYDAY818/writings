## linux知识
### 基础命令shell
#### 1.!! 使用刚才输入的命令
#### 2.alias 命令别名  alias li='ls -li' 
#### 3.环境变量
	printenv HOME 显示环境变量  ls $HOME 
	set 局部变量,全局变量,用户自定义变量 并排序
#### 4.有空格要用引号
```
	my_home = "hello world"
	echo $my_home
```
#### 5.export my_home   定义全局变量
       unset  my_home   删除
#### 6.添加path   PATH=$PATH:/home/christine/Scripts  
	PATH=$PATH:.  代表当前目录从  
退出或重启失效
#### 7./etc/profile   大部分linux默认bash shell启动文件
#### 8.bash shell 提供BASH_ENV环境变量 ``` printenv BASH_ENV ```
#### 9.大多数linux提供$HOME/.bashrc作为个人用户永久性bash shell变量
#### 10.useradd   添加用户 -G 加入组  userdel   删除用户
	usermod   修改账户  -l 登录名  -L 锁定 -U 解锁  -p 修改密码
	passwd   修改密码   -e  强制用户下次登陆修改密码
	cash  修改shell   
	chfn   修改passwd备注
	finger  查看用户信息(centos没有)
	chage  修改账户有效期
#### 11.chmod  
 ``` shown owner.group file 同时改变数组属主 ```
	chown 改变属主  
	chgrp 改变属组     
#### 12.fdisk 分区
	重新读取分区 partprob  或 hdparm 