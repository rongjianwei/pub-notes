x# commands of ubuntu

## ubuntu 命令：

1, 快捷键 alt+ctl+t：调出终端

2，ls：列出当前目录（常用参数 -l -r ）

3，nautilus + 路径：打开一个文件夹窗口

4，快捷键Tab：补全命令

5，cd + 目录：进入目录

6，mkdir：创建目录（常用参数 -p ）

7，touch：创建空白文件或改变文件或目录时间

8，echo：在终端输出显示字符（echo "xxx" > abc: 把xxx写入abc这个文件

9，cat：把文件内容显示到终端

10，vi 或者 vim + 文件名： 用vi 或者vim 打开文件

11，gedit

12，cp：复制文件或者目录（常用参数 -r -v -f)

13, rm: 删除文件或者目录（常用参数 -r -v -f)

14，mv： 移动文件或者目录

15，sudo + 命令：以root权限来进行命令操作，需要密码

16，su + 用户：切换到其他用户，如果不加用户则切换到root用户

17，chmod：改变文件权限（常用参数 -R），需要root权限

18, reboot：系统重启，需要root权限

19, shutdown: 关机，需要root权限(常用参数 now -h )

20, man + 命令：获得命令的使用方法

*******************************
vim从入门到放弃  
[http://blog.csdn.net/sumword_/article/details/53011463](http://blog.csdn.net/sumword_/article/details/53011463)

让VIM彻底告别乱码
[http://blog.csdn.net/smstong/article/details/51279810](http://blog.csdn.net/smstong/article/details/51279810)

****************************
### ubuntu 端口扫描，防火墙命令
	nmap
	ufw
	gufw

****************************
### ubuntu 下载工具[http://ugetdm.com/](http://ugetdm.com/)
    sudo apt install uget #安装
    uget-gtk #调用

****************************
### apt 常用命令
更新 apt 资源包，然后安装软件包  
    sudo apt update
    sudo apt upgrade

    apt search 程序包名  #搜索
    sudo apt-get install 程序包名 #安装

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
    dpkg -l | grep php #查看系统中已安装软件包信息, 显示全部包含 php 的软件包

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

    sudo apt install xsltproc
    sudo apt install docbook-xsl
    sudo apt install docbook-defguide

最后这个就是那本大名鼎鼎的Docbook:The Definitive Guide，装完之后就可以直接在本机浏览器输入[http://localhost/doc/docbook-defguide/html/docbook.html]( http://localhost/doc/docbook-defguide/html/docbook.html )来阅读此书了，我们和谐社会不是不能访问docbook.org吗，装完这个就可以本机阅读了，当然，你得装了apache。

*************************
### ubuntu中的压缩与解压缩

    sudo tar xzvf drush-8.x-6.0-rc4.tar.gz  #解压缩 tar 命令
    sudo tar czvf 文件名.tar.gz 目标名  #压缩 tar 命令

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
以下两项可以在系统安装时，选择加入。  
    sudo apt-get install lamp-server^   
    sudo apt install openssh-server

for deepin 15.7
    sudo apt install openssh-server
    

*****************************************
### Ubuntu下安装使用Xfce4 桌面环境  

    sudo apt-get install xubuntu-desktop  
安装图形界面之后，在图形界面下，settings/language support 安装中文支持。 输入法选择 fcitx 。如果没有，用 apt 命令安装。
打开 settings/language support 把键盘输入法系统改成 fcitx 。
登出(Log out) 你的计算机，然后重新登陆。
打开任务中的输入法图标，选择设置，点击输入输入法这一栏的最底下找到 “+” 按钮，并在弹出的窗口中取消 “只显示当前语言” 的复选框，在搜索栏中查找 “Sogou Pinyin”，并添加。
    sudo apt install wicd #无线网卡管理

安装 mysql workbench  
    sudo apt-get install mysql-workbench  

安装 phpmyadmin  
    sudo apt install phpmyadmin #注意安装位置，可以用 whereis 命令查看。 然后在 /var/www/html 目录中设定 ln -s 虚拟目录。  


安装搜狗汉字输入法  
[https://pinyin.sogou.com/linux/](https://pinyin.sogou.com/linux/)

ubuntu 16.04 lts 怎样安装搜狗输入法  
    sudo apt-get install fcitx fcitx-libs  
    sudo dpkg -i sogoupinyin_xxx.deb

	sudo apt install fcitx-table-wbpy #搜狗安装失败，替代品

参考：  
[https://zhidao.baidu.com/question/330470557468596205.html?qbl=relate_question_0](https://zhidao.baidu.com/question/330470557468596205.html?qbl=relate_question_0)
******************************************************
### Ubuntu 16.04下安装64位谷歌Chrome浏览器

    sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/
    wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
    sudo apt-get update
    sudo apt-get install google-chrome-stable
    /usr/bin/google-chrome-stable
    
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

    find /etc -name "*" | grep "hello abcserver"
    find /etc -name "*" | grep "hello abcserver" > ./cqtest.txt


