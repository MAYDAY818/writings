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
	挂载 mount(重启失效)  可添加/etc/fstab

#### 13.fsck分区修复
#### 14.命令替换
```
`data`
$(data)
```
#### 15.重定向
输入重定向 
```
wc < test6
```
输出重定向
```
command > outputfile
```
内联输入重定向(规定输入结尾)
```
command << marker
>data
>marker
```
#### 16.计算
```
expr 5*2

$[1 + 5]

$[$var1 * ($var2 - $var3)]
```
浮点运算
```
bc -q
//设置小数位个数
scale=4
//shell使用
var1=$(echo "scale=4;3.44 / 5" | bc)
```
大量计算
```
#!/bin/bash

var1=10.46
var2=43.67
var3=33.2
var4=71

var5=$(bc << EOF
scale = 4
a1 = ($var1 * $var2)
b1 = ($var3 * $var4)
a1 + b1
EOF
)
```

#### 17.退出脚本
```$?```上一个命令的退出状态码(0-255)
```
0，成功
126，不可执行  
127，没有找到命令  
128，无效的退出参数  
130，ctrl+c退出  
1，未知错误  
```

##### 自定义exit

#### $\color{red}{18.if-then}$
```
if command
then
	commands
else
	commands
fi
```

```
if command1
then
	commands
elif command2
else
	commands
fi
```

test测试的一系列参数和值  
不写condition会以非0的退出状态码退出，并执行else
```
if test condition
then
	commands
else
	commands
fi
```

```
if [ condition ]
then
	commands
else
	commands
fi
```
#### $\color{red}{19.比较}$
bash shell只能进行整数计算
```
-eq	相等
-ge	大于等于
-gt	大于
-le	小于等于
-lt	小于
-ne	不等于
```
字符串比较
```
=
！=
//大于小于必须转义,大写字母小于小写字母
\>
\<
```
-n和-z判断变量是否有数据

```
-e filename 如果 filename存在，则为真 [ -e /var/log/syslog ]
-d filename 如果 filename为目录，则为真 [ -d /tmp/mydir ]
-s filename 存在并非空
-O filename 存在并属于当前用户
-G fielname 存在并且默认组与当前用户相同
-f filename 如果 filename为常规文件，则为真 [ -f /usr/bin/grep ]
-L filename 如果 filename为符号链接，则为真 [ -L /usr/bin/grep ]
-r filename 如果 filename可读，则为真 [ -r /var/log/syslog ]
-w filename 如果 filename可写，则为真 [ -w /var/mytmp.txt ]
-x filename 如果 filename可执行，则为真 [ -L /usr/bin/grep ]
filename1 -nt filename2 如果 filename1比 filename2新，则为真 [ /tmp/install/etc/services -nt /etc/services ]
filename1 -ot filename2 如果 filename1比 filename2旧，则为真 [ /boot/bzImage -ot arch/i386/boot/bzImage ]
```

```
[ condition1 ] && [ condition2 ]
[ conditionl ] || [ condition2 ]
```

```
(( 高级数学公式 ))
++ -- ! ~ ** << >> & | && ||
(( vla2 = val1 ** 2 ))
```

```
[[ 模式匹配 ]]
```
#### $\color{red}{20.case}$
```
case variable in
pattern1 | pattern2) commands1;;
pattern3) commands;;
*) default commands;;
esac
```
#### $\color{red}{21.for}$
```
for var in list	//list有空格应使用""括起来
do 
	commands
done
//使用\转义，或者"New York"引起来
//更改字段分隔符 内部字段分隔符IFS
IFS=$'\n'
IFS=:
//多个IFS字符
IFS=$'\n':"

//保证IFS仅在此次脚本中被修改
IFSOLD=$IFS
IFS=$'\n'
<代码>
IFS=$IFS.OLD
```
```
for(( a = 1; a < 10; a++ ))
do
	commands
done
```
#### $\color{red}{22.while}$
```
while test command
do	
	other commands
done
```
#### $\color{red}{23.until}$
指定返回非0的状态码，只要不是0，就会执行循环中的命令
```
until test commands
do
	other commands
done
```

#### $\color{red}{24.break}$
```
//跳出几层循环，默认1
break n
```

#### $\color{red}{24.continue}$


#### $\color{red}{25.done}$
```
//循环完成后可以将打印结果重定向到文件中（管道）
done > test.txt
done | sort
```

#### $\color{red}{26.用户输入}$
```
//如果参数有空格，需要引号括起来
$0	//程序名
//返回脚本名，忽略脚本路径
name=$(basename $0 )
$1	//第一个参数
$2
······
$9
${10}

//判断参数是否存在
[ -n $1 ]

//参数个数
$#
//${} 括号内禁止使用$
//最后一个参数${!#}


//$* 会把所有参数当成一个参数
//$@ 会单独处理每个参数

//shift 会移动参数，第二个变为第一个，但第一个永远是程序名
shift 2
```