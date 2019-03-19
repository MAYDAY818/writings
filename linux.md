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
#### 8.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      