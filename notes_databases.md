##mysql的安装与命令



## postgreSql的安装与命令

### 1 安装方法摘要：
A）Ubuntu 系统下安装：

       sudo apt install postgresql postgresql-contrib
       sudo apt install phppgadmin pgadmin3
       
B）windows 系统下安装:


C) 两种图形操作界面：
phppgadmin pgadmin3


### 2 命令行登录数据库

有两种方式，一是直接在系统shell下执行psql命令；而是先进入psql环境，然后再连接数据库。下面分别给出实例：
A)直接登录

执行命令：psql -h 172.16.35.179 -U username -d dbname ，其中username为数据库用户名，dbname为要连接的数据库名，执行后提示输入密码如下：
Password for user username: （在此输入密码）

输入密码后即可进入psql环境了。
B) 切换数据库
有时候需要在psql环境下切换数据库，此时执行如下psql命令：
\c dbname username serverIP port
其中除了数据库名外，其他的参数都是可选的，如果使用默认值可以使用-作为占位符
执行这个命令后，也是提示输入密码。

### 3 查看帮助
psql提供了很好的在线帮助文档，总入口命令是help，输入这个命令就可以看到

       vsb9=# help
       You are using psql, the command-line interface to PostgreSQL.
       Type:  \copyright for distribution terms
              \h for help with SQL commands
              \? for help with psql commands
              \g or terminate with semicolon to execute query
              \q to quit

可以看到，标准SQL命令的帮助和psql特有命令的帮助是分开的。输入\?查看psql命令，会发现所有的psql命令都是以\开头，这就很容易和标准的SQL命令进行区分开来。

### 4 常用命令
为了便于记忆，这里把对应的mysql命令也列出来了。

#### (1)列出所有的数据库
mysql: show databases        
psql: \l或\list        
#### (2)切换数据库
mysql: use dbname    
psql: \c dbname      

#### (3)列出当前数据库下的数据表
mysql: show tables   
psql: \d

#### (4)列出指定表的所有字段
mysql: show columns from table name       
psql: \d tablename   

#### (5)查看指定表的基本情况
mysql: describe tablename   
psql: \d+ tablename  

#### (6)退出登录
mysql: quit 或者\q     
psql:\q

##sqlite数据库

https://www.sqlite.org/index.html
https://sqlitestudio.pl/

SQlite入门 http://www.runoob.com/sqlite/sqlite-tutorial.html

##go语言环境的设置

https://blog.csdn.net/gongpulin/article/details/80972806

方法1(亲测有效): gopm 代替go 下载第三方依赖包

可以采用gopm从golang.org一些镜像网站上下载。 
a). 安装gopm

go get -u github.com/gpmgo/gopm

    1

b). 用gopm get -g代替go getgopm get 
不采用-g参数，会把依赖包下载.vendor目录下面； 
采用-g 参数，可以把依赖包下载到GOPATH目录中；

gopm get -g golang.org/x/net  

##golang 开机启动

https://www.golangtc.com/t/57108dd6b09ecc66b900032a 

可以看看这个包 https://github.com/takama/daemon 

https://www.linuxidc.com/Linux/2017-09/147166.htm 


Go语言daemon启动的解决方法.linux平台 https://blog.csdn.net/fyxichen/article/details/50541449 

golang以daemen后台形式运行 https://blog.csdn.net/lsm135/article/details/78947113 

Ubuntu - screen 命令工具 https://www.aiuai.cn/aifarm791.html

##golang https服务器

go与https https://www.cnblogs.com/pzblog/p/9088286.html

golang中使用HTTPS以及TSL(.crt、.key、.pem区别以及crypto/tls包介绍) https://studygolang.com/articles/10776


##screen命令

 https://www.cnblogs.com/ywl925/p/3604530.html

