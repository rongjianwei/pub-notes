# commands of ubuntu

## ubuntu 命令：
****************************
### ubuntu 下添加/删除启动服务  
1.添加一个服务：
    $sudo update-rc.d ServiceName default  
2.删除一个服务：
    $sudo update-rc.d ServiceName remove

在Linux系统下，一个Services的启动、停止以及重启通常是通过/etc/init.d目录下的脚本来控制的。
然而，在启动或改变运行级别时，是在/etc/rcX.d中来搜索脚本。其中X是运行级别的number。


### ubuntu软件安装(pkg安装)
 
    apt-get install softname1 softname2 softname3……  #pkg安装
    apt-get remove softname1 softname2 softname3……  #卸载软件
    apt-get remove --purge softname1  #卸载并清除配置
    apt-get update #更新软件信息数据库
    apt-get upgrade  #进行系统升级
    apt-cache search softname1 softname2 softname3……  #搜索软件包

Deb软件包相关安装与卸载
 
    dpkg -i xxx.deb  #安装deb软件包
    dpkg -r xxx.deb #删除软件包
    dpkg -r --purge xxx.deb #连同配置文件一起删除
    dpkg -info xxx.deb #查看软件包信息
    dpkg -L xxx.deb  #查看文件拷贝详情
    dpkg -l  #查看系统中已安装软件包信息

**********************************
### 查看磁盘空间
    
Df命令是linux系统以磁盘分区为单位查看文件系统，可以加上参数查看磁盘剩余空间信息，命令格式：  

    df -hl #查看磁盘剩余空间
    df -h  #查看每个根路径的分区大小

    du -sh #[目录名] 返回该目录的大小
    du -sm #[文件夹] 返回该文件夹总M数

更多功能可以输入一下命令查看   
    
    df --help  
    du --help

*************************
### 准备 docbook 环境

    sudo apt-get install xsltproc
    sudo apt-get install docbook-xsl
    sudo apt-get install docbook-defguide

最后这个就是那本大名鼎鼎的Docbook:The Definitive Guide，装完之后就可以直接在本机浏览器输入http://localhost/doc/docbook-defguide/html/docbook.html来阅读此书了，我们和谐社会不是不能访问docbook.org吗，装完这个就可以本机阅读了，当然，你得装了apache。

*************************
### ubuntu中的压缩与解压缩

    sudo tar xzvf drush-8.x-6.0-rc4.tar.gz  #解压缩 tar 命令
    sudo tar zcvf 文件名.tar.gz 目标名  #压缩 tar 命令

unzip解压缩应用实例

    unzip test.zip  #1、把文件解压到当前目录下
    unzip -d /temp test.zip  #2、如果要把文件解压到指定的目录下，需要用到-d参数。
    unzip -n test.zip  #3、解压的时候，有时候不想覆盖已经存在的文件，那么可以加上-n参数
    unzip -n -d /temp test.zip
    unzip -l test.zip  #4、只看一下zip压缩包中包含哪些文件，不进行解压缩
    unzip -v test.zip  #5、查看显示的文件列表还包含压缩比率
    unzip -t test.zip  #6、检查zip文件是否损坏
    unzip -o test.zip -d /tmp/  #7、将压缩文件test.zip在指定目录tmp下解压缩，如果已有相同的文件存在，要求unzip命令覆盖原先的文件

**********************************
### 修改apache/conf/httpd.conf文件：
ubuntu apt安装中是 /etc/apache2/apache2.conf

1.将所有的AllowOverride None修改为AllowOverride All，一共有三处。

2.开启模块LoadModule rewrite_module modules/mod_rewrite.so，将#去掉即可。
ubuntu 中用命令 

    sudo  a2enmod 开启 rewriter 模块。

**********************************
### 修改 vim 的默认配色(来自百度经验)

查看Vim实例中当前的颜色主题  
打开一个Vim窗口，输入命令:color或:colorscheme后回车查看当前的颜色主题。  
得到Vim示例当前的颜色主题  
可以看到当前的颜色主题为default。  

Vim实例中设置颜色主题  
输入命令"colorscheme elflord (主题名字)"，即可设置当前vim实例的颜色主题。  

查看Vim的运行目录  
vim的颜色主题文件放在Vim运行目录下的color目录下，所以我们首先需要知道vim的运行目录。  
在vim中输入命令:echo $VIMRUNTIME 来查看Vim的运行目录。  
得到vim的运行目录  
从图中可以看到，vim的运行路径为/usr/share/vim/vim74::  

进入vim的运行目录，查看color目录下以“.vim”为结尾的文件  
这些文件即是颜色主题文件，文件名就是主题名字。  

修改vim配置文件，更改默认颜色主题  
打开/etc/vim/vimrc文件，在其中加入一行"colorscheme elflord (颜色主题名字)"，之后保存更改即可。  
**********************************
### ln软连接
    ln -s 源文件 目标文件

**********************************
### 更新 apt 资源包，然后安装软件包  
    sudo apt update
    sudo apt upgrade

### 安装 lamp 服务器组, openssh 服务器  
    sudo apt-get install lamp-server^  
	sudo apt install openssh-server

安装 mysql workbench  
    sudo apt-get install mysql-workbench  

*****************************************
### Ubuntu下安装使用Xfce4 桌面环境  

    sudo apt-get install xubuntu-desktop  

******************************************************
### Ubuntu 16.04下安装64位谷歌Chrome浏览器
[http://www.linuxidc.com/Linux/2016-05/131096.htm]( http://www.linuxidc.com/Linux/2016-05/131096.htm ) 

*****************************************************
### vi编辑器中的整行（多行）复制与粘贴就非常必要了。  
1、复制  
  1）单行复制  
  在命令模式下，将光标移动到将要复制的行处，按“yy”进行复制；
  2）多行复制  
  在命令模式下，将光标移动到将要复制的首行处，按“nyy”复制n行；其中n为1、2、3……
  2、粘贴  
  在命令模式下，将光标移动到将要粘贴的行处，按“p”进行粘贴

vi复制多行文本的方法  
  方法1：  
   光标放到第6行，  
   输入：2yy  
  光标放到第9行，  
   输入：p  #此方法适合复制少量行文本的情况，复制第6行（包括）下面的2行数据，放到第9行下面。  

  方法2：  
   命令行模式下输入  
   6,9 co 12  
   复制第6行到第9行之间的内容到第12行后面。  

  方法3：  
   有时候不想费劲看多少行或复制大量行时，可以使用标签来替代  
   光标移到起始行，输入ma  
   光标移到结束行，输入mb  
   光标移到粘贴行，输入mc  
   然后 :'a,'b co 'c   把 co 改成 m 就成剪切了  
   要删除多行的话，可以用 ：5, 9 de  

********************************************************
### 在某个路径下查找所有包含“hello abcserver”字符串的文件。

find /etc -name “*” | xargs grep “hello abcserver”

或者find /etc -name “*” | xargs grep “hello abcserver” > ./cqtest.txt


