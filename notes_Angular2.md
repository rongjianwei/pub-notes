#notes of Angular 2
## angular2 参考网站
[中文入门教程]( http://www.angularjs.cn/A2uA )

[angular2 官网]( https://angular.io/docs/ts/latest/ )  

[angular2 中文镜像]( https://angular.cn/ )

[Awesome Angular 2]( https://github.com/AngularClass/awesome-angular2 )

[angular2 education]( https://github.com/timjacobi/angular2-education )

[hotJS angular2 ]( https://www.hotjs.net/skills/angular2/resources )

[npm 淘宝镜像 ]( https://npm.taobao.org/ )
####你可以使用我们定制的 cnpm (gzip 压缩支持) 命令行工具代替默认的 npm。安装cnpm的操作：  
    $ npm install -g cnpm --registry=https://registry.npm.taobao.org
####安装模块
从 registry.npm.taobao.org 安装所有模块. 当安装的时候发现安装的模块还没有同步过来, 淘宝 NPM 会自动在后台进行同步, 并且会让你从官方 NPM registry.npmjs.org 进行安装. 下次你再安装这个模块的时候, 就会直接从 淘宝 NPM 安装了.  
    
    $ cnpm install [name]

####同步模块
直接通过 sync 命令马上同步一个模块, 只有 cnpm 命令行才有此功能:
    
    $ cnpm sync connect
####当然, 你可以直接通过 web 方式来同步: /sync/connect
    
    $ open https://npm.taobao.org/sync/connect
####其它命令
支持 npm 除了 publish 之外的所有命令, 如:
    
    $ cnpm info connect

[node 下载 ]( https://nodejs.org/en/download/ )

###node安装：Debian and Ubuntu based Linux distributions

Also including: Linux Mint, Linux Mint Debian Edition (LMDE), elementaryOS and others.

Node.js is available from the NodeSource Debian and Ubuntu binary distributions repository (formerly Chris Lea's Launchpad PPA). Support for this repository, along with its scripts, can be found on GitHub at nodesource/distributions.

NOTE: If you are using Ubuntu Precise or Debian Wheezy, you might want to read about running Node.js >= 6.x on older distros.

    curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
    sudo apt-get install -y nodejs

Alternatively, for Node.js v7:

    curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash -
    sudo apt-get install -y nodejs

Optional: install build tools

To compile and install native addons from npm you may also need to install build tools:

    sudo apt-get install -y build-essential

Available architectures:

i386 (32-bit)
amd64 (64-bit)
armhf (ARM 32-bit hard-float, ARMv7 and up: arm-linux-gnueabihf)

Supported Ubuntu versions:

Ubuntu 12.04 LTS (Precise Pangolin)
Ubuntu 14.04 LTS (Trusty Tahr)
Ubuntu 16.04 LTS (Xenial Xerus)

###揭秘angular2 互动出版社  
[http://blog.csdn.net/chinapub_2009/article/details/54090612]( http://blog.csdn.net/chinapub_2009/article/details/54090612 )


#note for ionic 

[ionic 官方网站]( http://ionicframework.com/ )

[ionic 官方文档](http://ionicframework.com/docs/ )

[Github 地址]( https://github.com/driftyco/ionic )