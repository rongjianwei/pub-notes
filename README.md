# pub-notes
共享的技术笔记
##目录
[drupal笔记]( ./notes_drupal.md "drupal学习笔记" )    
[ubuntu 常用命令]( ./cmds_ubuntu.md "ubuntu 常用命令" )  
[Angular2笔记]( ./notes_Angular2.md "Angular2学习笔记" )  


##网络技术相关的参考链接
###Atom
https://atom-china.org/  
https://cnpmjs.org/mirrors/atom/  
https://atom.io/  

###PHP7教程
[http://www.yiibai.com/php7/]( http://www.yiibai.com/php7/ )

###Markdown
[Markdown语法说明（简体中文)]( http://www.appinn.com/markdown/ "Markdown" )  
This is [an example]( http://example.com/ "Title") inline link.  
[This link]( http://example.net/ ) has no title attribute.

###SQL数据库
https://www.postgresql.org/  
http://www.postgres.cn/index.php/home

###NoSQL 数据库
[monogoDB 中文社区]( http://www.mongoing.com/ )  
https://www.mongodb.com/

http://www.redis.cn/  
http://www.redis.net.cn/  
https://redis.io/  

http://memcached.org/  

###阿里短信  
http://www.alidayu.com/

**************************************************************************

##其他：
###phpMyadmin默认也提供了访问控制功能，具体配置如下：

进入phpMyAdmin目录，找到config.inc.php，如果没有，可以将根目录下的config.sample.inc.php复制为config.inc.php。

编辑config.inc.php，添加下面两行代码，其中192.168.0.1是允许访问 phpMyAdmin 的IP，Access denied是未经授权访问时的提示信息：

    $ip_prefix = '192.168.0.1';
    if (substr($_SERVER['REMOTE_ADDR'], 0, strlen($ip_prefix)) != $ip_prefix ) die('Access denied');

允许域名访问
    
    $ip_prefix = gethostbyname('1q573837u7.51mypc.cn');
    if (substr($_SERVER['REMOTE_ADDR'], 0, strlen($ip_prefix)) != $ip_prefix ) die('Access denied');


************************
###蓝灯项目
https://github.com/getlantern/lantern  
    
	sudo dpkg -i lantern-installer-beta-64-bit.deb

********************************
###腾讯云工程师 :
2016-11-24 18:20:11

您好，关于微信开放/公众平台的业务合作，您可以发送邮件到 weixin-open@qq.com 进行商谈，感谢您的支持！ 
 或者请咨询这里的微信在线客服 http://kf.qq.com/other/for_your_service.shtml
您也可以到http://weixin.qq.com/-- 联系我们，里面有一些联系方式，您参考一下。

*************************
###51cto学院
[http://edu.51cto.com/](http://edu.51cto.com/)  

###豆瓣读书  
[https://book.douban.com/](https://book.douban.com/)

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
