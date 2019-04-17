

电脑 thinkpad t460p i7-7600HQ  2.6GHz  8核
    内存 4+8
    机械硬盘500G
    
    机械硬盘速度过慢，内存占4G，cpu 100%
    一加3  1:15:28+1:42:49=2:57:50    //中断，继续
    一加2  2:13  //完整
###常用操作
 
清理
make clean 
清理更加严格
make clobber
 
忽略本地强制更新
repo forall -c 'git reset --hard; git clean -f -d -x'

####ubuntu 1804 环境  kubuntu 1810 测试成功

jdk以及python默认安装，请使用java-version以及python查询，jdk默认为8

sudo apt-get install libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-dev g++-multilib 
sudo apt-get install -y git flex bison gperf build-essential libncurses5-dev:i386 
sudo apt-get install tofrodos python-markdown libxml2-utils xsltproc zlib1g-dev:i386 
sudo apt-get install dpkg-dev libsdl1.2-dev libesd0-dev
sudo apt-get install git-core gnupg flex bison gperf build-essential  
sudo apt-get install zip curl zlib1g-dev gcc-multilib g++-multilib 
sudo apt-get install libc6-dev-i386 
sudo apt-get install lib32ncurses5-dev x11proto-core-dev libx11-dev   //需要某些依赖，可以是使用aptitude
sudo apt-get install libgl1-mesa-dev libxml2-utils xsltproc unzip m4
sudo apt-get install lib32z-dev ccache


###步骤(根据导演论坛教程)

1.下载清华 REPO构建工具
mkdir ~/bin
PATH=~/bin:$PATH
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo

2.cd 代码存放目录路径
请使用特殊方式下载
repo init -u https://github.com/MoKee/android -b mkp --depth 1
请耐心等待
repo sync
3.构造环境
. build/envsetup.sh  //无效使用source .build/envsetup

4.加载所要构造机型配置
lunch mk_osborn-userdebug
5.开始编译
mka bacon  //可以使用make -j8 bacon来编译，8为线程

6.请耐心等待
完成后在out文件中查找
