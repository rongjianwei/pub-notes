# notes of drupal  
## drupal8 更新（updating）步骤
更新（updating）的含义是小版本更新(例如8.01 至 8.2.4), 我们使用的两个命令程序协助更新，具体的版本如下：  
composer 版本：1.0.0-beta2  [composer 中文网 ](http://www.phpcomposer.com/) (有关国内的镜像，大大提高update的速度)  
drush 版本：9.1.0  
我们使用这两个命令操作，可以大幅度提高工作效率。 提别提醒，各种更新操作，要先在测试网站上操作，做到万无一失之后，才能在生产（production）网站上操作。 

### 首先更新模块
1）备份网站程序文件，备份网站数据库文件：

    sudo tar zcvf 备份文件名.tar.gz 网站程序文件目录  #压缩打包后保存

    TODAY0=$(date +%Y-%m-%d)
    mysqldump --defaults-extra-file="temp.cnf" --user=fox  --max_allowed_packet=1G --host=127.0.0.1 --port=3306 --default-character-set=utf8 --single-transaction=TRUE "网站数据库名" > "./${TODAY0}网站数据库名_backup.sql" #备份网站数据库，形成一个 sql 文件。

2）以 Admin（用户1）的身份登陆网站。 


3）选择以下的功能：管理（Manage）->扩展（Extend） ->更新（Update）, 查看有哪些某块需要更新。 参照更新提示，复制 composer require 命令。 然后在命令行窗口运行该 composer 命令，注意这个命令行窗口的当前目录必须是网站的主目录：

    composer require 'drupal/profile:^1.0' #实例

5）每个模块更新之后，尝试更新数据库： 
 
    drush updatedb #更新数据库
    drush cr #必要时清除缓冲区

5）然后进入网站测试一下，如果运行正常，返回 2）继续更新模块，直至全部完成。


6）如果发现某个模块更新有问题做记录，这个出错的模块，暂时不能更新。有了新的版本以后再说。



### 其次更新 drupal8 内核
下面的更新步骤，试验失败。最后采用的是 core/UPDATE.txt 文件中叙述的更新 drupal8 内核方法。2018-2-17

1）备份网站程序文件，备份网站数据库文件：

    sudo tar zcvf 备份文件名.tar.gz 网站程序文件目录  #压缩打包后保存

    TODAY0=$(date +%Y-%m-%d)
    mysqldump --defaults-extra-file="temp.cnf" --user=fox  --max_allowed_packet=1G --host=127.0.0.1 --port=3306 --default-character-set=utf8 --single-transaction=TRUE "网站数据库名" > "./${TODAY0}网站数据库名_backup.sql" #

2）将网站转入维护模式（Activate maintenance mode）：

    drush sset system.maintenance_mode 1

3）清除缓冲区（cache):

    drush cr

4）更新全部程序：

    composer update 

5）更新数据库，清除缓冲区（cache):

    drush updatedb
    drush cr

7）将网站转入上线模式：

    drush sset system.maintenance_mode 0

8）测试网站，万一不能正常运行，用备份的文件恢复“网站程序文件，恢复数据库”。


## drupal使用函数  
### drupal抓取外部网络图像  
    
    function get_external_image($url) {
    $external_image = file_get_contents($url);
    $parsed_url = parse_url($url);
    $name_dest = rand(1000,9999)."_". basename($parsed_url["path"]);
    var_dump($name_dest );
    $file = file_save_data($external_image, 'public://'.$name_dest , FILE_EXISTS_REPLACE);
    if (is_object($file) && file_exists($file->uri)) {
        $file->status = 1;
        $file = file_save($file);
        drupal_write_record('file_usage', $file);
        return (array) $file;
    }
    return null;
    }
    
    get_external_image("http://hs-album.oss.aliyuncs.com/static/99/18/ae/image/20161027/20161027205558_38107.jpg");

    get_external_image("http://hs-album.oss.aliyuncs.com/static/99/18/ae/image/20161027/20161027205923_25011.jpg");

    get_external_image("http://hs-album.oss.aliyuncs.com/static/99/18/ae/image/20161027/20161027210056_75054.jpg");

    get_external_image("http://hs-album.oss.aliyuncs.com/static/99/18/ae/image/20161027/20161027210238_47369.jpg");

    get_external_image("http://hs-album.oss.aliyuncs.com/static/99/18/ae/image/20161027/20161027210517_58958.jpg");

    get_external_image("http://hs-album.oss.aliyuncs.com/static/99/18/ae/image/20161027/20161027113827_81711.png");

    get_external_image("");

    get_external_image("");

    get_external_image("");

    get_external_image("");

    get_external_image("");

 
## 在ubuntu 16.04系统上，安装drupal8
### 运行环境的准备
安装lamp  
    apt-get install lamp-server^  
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

monogoDB  
https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/  
[Ubuntu16.04使用阿里云镜像安装Mongodb]( http://www.linuxdiyf.com/linux/26151.html )  
    sudo apt-get install php-mongodb  
[http://drupalchina.cn/content/shi-yong-mongodb-jia-su-drupal7-field-cun-chu]( http://drupalchina.cn/content/shi-yong-mongodb-jia-su-drupal7-field-cun-chu )  
www.wiredcraft.com
我是
JackeyChan
Email: a397420507@gmail.com
qq: 397420507

composer  
drush  

****************************
### JavaScript
JavaScript 参考文档  ( https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference )  
https://www.javascript.com/   
http://www.itxueyuan.org/  
http://www.w3school.com.cn/js/index.asp  

****************************
### d8 database api
https://www.drupal.org/docs/8/api/database-api  

****************************
### ubuntu 下添加/删除启动服务
1.添加一个服务：$sudo update-rc.d ServiceName default  
2.删除一个服务：$sudo update-rc.d ServiceName remove

在Linux系统下，一个Services的启动、停止以及重启通常是通过/etc/init.d目录下的脚本来控制的。
然而，在启动或改变运行级别时，是在/etc/rcX.d中来搜索脚本。其中X是运行级别的number。

****************************
### ubuntu 14.04下安装 tomcat7
sudo apt-get update
sudo apt-get install tomcat7  
安装辅助工具  
sudo apt-get install tomcat7-docs tomcat7-examples tomcat7-admin

验证安装成功：在浏览器上输入，服务器网址:8080，可以看到tomcat 的启动网页。

Tomcat默认安装目录：/etc/tomcat7，/usr/share/tomcat7，

********************************
sudo apt-get install solr-common


在/etc/tomcat7/Catalina/localhost下面创建一个solr.xml文件，内容如下：  

    <?xml version="1.0" encoding="utf-8"?>
    <Context docBase="/usr/share/tomcat7/webapps/solr" debug="0" crossContext="true">
    <Environment name="solr/home" type="java.lang.String" value="/usr/share/tomcat7/webapps/solr" override="true"/>
    </Context>

sudo service tomcat7 restart
正常重启之后在/var/lib/tomcat7/webapps目录下会增加一个solr目录

在/var/lib/tomcat7/webapps/solr下面，创建两个目录solr，navigation,将/usr/share/solr下面的文件，分别上传到这两个目录下面：

其实创建一个就够了，创建两个的目的，是将solr目录留作它用。

在/var/lib/tomcat7/webapps/solr下面，创建solr.xml文件，内容如下：

    <?xml version="1.0" encoding="UTF-8" ?>

    <!--
     All (relative) paths are relative to the installation path

      persistent: Save changes made via the API to this file
      sharedLib: path to a lib directory that will be shared across all cores
        -->
    <solr persistent="false">

    <!--
      adminPath: RequestHandler path to manage cores.  
        If 'null' (or absent), cores will not be manageable via request handler
      -->
    <cores adminPath="/admin/cores">
    <core name="solr" instanceDir="solr" />
    	<core name="navigation" instanceDir="navigation" />
    </cores>
    </solr>

重启tomcat7:
service tomcat7 restart

*******************************
### 安装solr，solr下载地址：
http://www.apache.org/dyn/closer.cgi/lucene/solr/  
如果已经安装 java8 的版本，下载最新的 solr-6.3.0版本。  
java7，对应下载 solr-5.5.3

下载后，保存到 /usr/local/share，然后解压缩.  
测试, 启动solr服务， sudo solr-5.5.3/bin/solr start
看到服务 solr 正常运行信息后， 在浏览器里输入，服务器ip:8983/solr, 即可看到 solr 的启动页面了。  

安装 solr 服务，运行 solr-5.5.3/bin/install_solr_service.sh , 详细操作，参见该脚本。

****************************
### 在ubuntu 16.04下安装 composer

[composer 中文网 ](http://www.phpcomposer.com/) (有关国内的镜像，大大提高update的速度)

1)下载
从网站 https://getcomposer.org/download/ ,下载 composer.phar 文件，然后复制到：
/usr/local/share/composer 目录
还有一种下载方法(可能无法突破墙)： curl -sS https://getcomposer.org/installer | php

2) 安装
php composer.phar --version
composer程序启动后，会显示版本号。

3) 设置全局命令
sudo mv composer.phar /usr/local/bin/composer
sudo chmod 755 /usr/local/bin/composer

4) 查看是否安装成功
composer -version
如果成功的话，会出现一个华丽的图标：composer 等等。

*5)还有种方法，执行安装composer的php脚本： 

    sudo php install
    install 运行成功后，转到2)-4)执行相应的步骤。

*6)还有种方法  
# 1.6.0版下载安装后,运行有问题, 采用apt安装 1.0.0 beta2 版本
    sudo apt install composer
    composer --version #测试安装是否成功
    sudo composer config -g repo.packagist composer https://packagist.phpcomposer.com #国内镜像

**********************************
### 通过 composer 安装 drush
    composer global require drush/drush #master 版本 8.x
    sudo ln -s /home/rjw/.composer/vendor/drush/drush/drush  /usr/bin/drush
    composer remove drush/drush  

**********************************
### 通过 composer 安装 drush (github 源代码)

1)把在 Github 上的 Drush 克隆一份到本地的 /usr/local/src/drush 这个目录的下面。然后进入到这个目录：
drush 8.x 兼容 d6, d7, d8

    sudo git clone -b 8.x https://github.com/drush-ops/drush.git /usr/local/src/drush
    cd /usr/local/src/drush

2)执行 composer install 去安装 Drush 所依赖的东西，可能会提示输入你在 github 上的用户名与密码：
	
	sudo composer update
	sudo composer install

成功以后，在环境变量的目录下面创建一个 drush 的快捷方式，可以使用 ln -s  去做这件事，像这样：

    sudo ln -s /usr/local/src/drush/drush /usr/bin/drush

现在你应该可以在系统的任何地方使用 drush 命令了：

    drush help
    drush --version

3)Run composer update

    sudo cd /usr/local/src/drush
    sudo composer update

4)卸载drush Uninstall with :

    composer global remove drush/drush

****************************
### 安装drupal控制台
[drupalconsole官网](https://drupalconsole.com/)

****************************
### 采用drush 更新drupal7 核心程序
https://www.drupal.org/node/2550801

****************************
[https://www.drupal.org/node/2700999](https://www.drupal.org/node/2700999)

****************************
### Drupal 7 - All About Rules
https://www.drupal.org/node/1866108

*********************************
###在Drupal项目中，网站被关闭的时候，页面仅显示关闭信息，若要进行用户登录，在网址后面加上'/user/login'，进入登录页面，例如：

网站的地址是：http://demo.com，要在网站关闭后进行用户登录，则在地址栏上输入：http://demo.com/user/login 或者 http://demo.com/?q=user 即可

*************************

## 参考网址与线索
*************************
Drupal 8 中文教程：从入门到精通  
[https://www.lugir.com/drupal8](https://www.lugir.com/drupal8)  

Drupal项目社区
[https://www.drupalproject.org/](https://www.drupalproject.org/)

亚艾元 [http://www.yaiyuan.com/](http://www.yaiyuan.com/)  

***************************
### 云客drupal8源码分析
之数据库系统及其使用  
[http://blog.csdn.net/u011474028/article/details/52958786](http://blog.csdn.net/u011474028/article/details/52958786)  
之服务器容器及symfony依赖注入组件  
[http://blog.csdn.net/u011474028/article/details/52623925](http://blog.csdn.net/u011474028/article/details/52623925)

*************************
### drupal8怎么使用外部数据库的数据  
https://zhidao.baidu.com/question/2271246971677217428.html

*************************
### 国外那些优秀的 Drupal 教程博客  
http://drupalct.org/drupal/drupal-tutorial-blogs-you-should-know.html

*************************
### drupal 8 入门  
http://blog.csdn.net/u011474028/article/details/52514472  
symfony中文  http://symfony.cn/docs/  
symfony官网 http://symfony.com/

*****************
### d8 建立客户模块
[https://www.drupal.org/docs/8/creating-custom-modules]( https://www.drupal.org/docs/8/creating-custom-modules )


**************************
### drush 开发网站
https://github.com/drush-ops/drush/

***************************************
### 关闭 clean url
    drush vset clean_url 0 --yes

***************************************
### 配置Clean URL

修改apache/conf/httpd.conf文件：
ubuntu apt安装中是 /etc/apache2/apache2.conf

1.将所有的AllowOverride None修改为AllowOverride All，一共有三处。

2.开启模块LoadModule rewrite_module modules/mod_rewrite.so，将#去掉即可。
ubuntu 中用命令

    sudo  a2enmod 开启 rewriter 模块。

*********************************************
### drupal8 创建上传目录

    mkdir  /var/www/drupal8/sites/default/files/
    sudo chown -Rvf www-data:www-data  /var/www/drupal8/sites/default/files
    sudo setfacl -R -m u:www-data:rwx -m u:firehare:rwx /var/www/drupal8/sites/default/files
    sudo setfacl -dR -m u:www-data:rwx -m u:firehare:rwx /var/www/drupal8/sites/default/files

将该上传目录用户设为www-data主要是为了让Drupal能够知道它对该目录有读写的权限，以便在做带宽优化时可以合并和压缩CSS，否则的话该功能不能正常。setfacl 语句的作用就是让www-data（Apache2用户名）和firehare（您的用户名）对该上传目录都有权限。如果该命令不起作用，可以百度一下，在/etc/fstab文件中的相关目录添加acl属性即可。这里就不再多讲了。
上述方法无效，改为 chmod 777 .

*************************************
### apt安装php5.6 php7.0 双系统，可以切换。
https://launchpad.net/~ondrej/+archive/ubuntu/php

    sudo apt-get install -y language-pack-en-base
    sudo apt-get install software-properties-common
    sudo LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php
    sudo apt update

    sudo apt-get install php5.6 php5.6-mysql php5.6-dom php5.6-gd php5.6-mbstring
    sudo apt-get install php7.0 php7.0-mysql php7.0-dom php7.0-gd php7.0-mbstring

    sudo a2dismod php7.0
    sudo a2dismod php5.6
    sudo service apache2 restart
通过网页测试，切换正常。

Verify your PHP's version  

    sudo php -v

安装 xdebug 调试
    sudo apt-get install php7.0-xdebug

drupal调试  
https://martsie.github.io/2014/04/02/drupal-xdebug-debugging/

**************************************************************************
### My Top 10 Drush commands

A beginner's Guide to Drush
drush 安装；sudo apt-get install drush

Think in Drupal

TVDrupal.com


### 源码分析博客
http://blog.sina.com.cn/s/blog_5a8b8eb80100r8pg.html

drupalproject.org

******************
### 有用的drupal 模块：
mudule_filter, locale, localization_update(l10n_update),
features， strongarm, l10n update, smtp，
wechat, wechat_views,

****************************

### 常用链接

Drupal 7 - All About Rules  https://www.drupal.org/node/1866108

Tutorials and site recipes 增加 https://www.drupal.org/node/627198

https://www.drupal.org/docs/7/modules/views/views-howtos

http://www.drupalla.com/ 猪跑啦

http://drupalct.org

http://www.aptana.com/products/studio3/download

http://www.drupalnotes.cn

QQ: 552382568

drupal7系统的API   https://api.drupal.org/api/drupal/7.x

field字段的API  https://api.drupal.org/api/drupal/modules%21field%21field.module/group/field/7.x



*****************************************************************

微盟的后台 http://www.weimob.com/website/login.html

www.airtable.com

tomcat7 http://115.28.56.194:8080/

solr服务 http://115.28.56.194:8983/solr

solr5.5.3 文档   http://lucene.apache.org/solr/5_5_3/index.html

http://www.thinkindrupal.com/

豆瓣阅读： thinkindrupal  https://read.douban.com/reader/ebook/15377941/


*******************************
《Beginning Drupal 8》  https://github.com/drupalchina/beginningd8cn

Markdown window 推荐用：http://markdownpad.com/
https://guides.github.com/features/mastering-markdown/

********************************
秦海   www.qhjhtf.com  华纺1-4-503，13910122949，QQ 598158521 

 HOOTIM 皓庭新风   www.haotingkeji.com
