# WordPress博客搭建

## 准备工作

1. 购买云服务器
2. 下载安装XShell（远程连接服务器）| 或者使用腾讯云网页”登录”连接服务器
3. 下载安装WinSCP（远程连接服务器可视化文件管理）


### 使用腾讯云网页登录服务器后台：（或者使用XShell，方便稳定）
 
*登录界面*

![](http://p7dwnxgqw.bkt.clouddn.com/img/2018/%E8%85%BE%E8%AE%AF%E4%BA%91%E5%90%8E%E5%8F%B0.png)




## 部署网站

推荐两个傻瓜式教程：（两个教程中都有些地方有错误）
>  https://www.cnblogs.com/DarrenChan/p/6622233.html

> https://www.cnblogs.com/flankershen/p/7476415.html

两个教程结合使用

****

## 安装步骤详解
### 环境
* 服务器操作系统：CentOS
*	博客部署服务器：Apache httpd
*	后台语言：PHP
*	数据库：MariaDB
*	前端框架：WordPress

### 步骤
#### 一、安装Apache
安装 Apache 很简单，只需要在终端输入以下命令就可以了：
> sudo yum install httpd


sudo 的意思是用 root 用户做什么操作，yum install 是在线安装；然后输入 yes 就确认下载安装了。

安装完毕之后我们需要启动服务：
> sudo service httpd start
> 

当启动服务器完成之后，先别着急往下弄，可以直接在浏览器中输入服务器的 ip 地址，应该就可以看到 Apache 的欢迎页面了。

>This page is used to test the operation of the Apache HTTP server after it has been installed…

如果你的 ip 地址已经和域名绑定了，那么在浏览器中输入你的域名也可以访问了，是不是很酷，就是这么简单，咱们继续。


#### 二、安装 MariaDB
安装 MariaDB
> yum install mariadb-server mariadb 

> systemctl start mariadb

通过上面的命令就可以安装并启动了数据库，安装数据库的时候会询问你一些简单的配置，输入 enter 和 yes 一路下来就 OK 了。

####  三、安装 PHP 以及相关 PHP 组件
先安装 PHP
> sudo yum install php php-mysql
> 
安装 PHP 相关组件
> yum install php-gd php-imap php-ldap php-odbc php-pear php-xml php-xmlrpc
> 

了解所有的 PHP 组件的话，可以使用如下命令搜索：
> yum search php-
> 


#### 四、开机默认启动 Apache 和 Mysql 服务(这里 CentOS 6 和 7 使用的是不同的命令行)
使用如下命令即可选择开机启动 Apache 和 MariaDB:
> systemctl enable httpd

> systemctl enable mariadb
 
可以用 service --status-all 来查看这两个进程是否启动。
 


#### 五、测试 PHP 是否安装成功
建立一个 info.php 文件：
> sudo nano /var/www/html/info.php

进入编辑模式，在文件中写入下面的 PHP 命令：
```
<?php
    phpinfo();
?>
 ```

然后Ctrl+O 保存，Ctrl+X退出。

在浏览器中输入 “IP地址/info.php”，例如：119.29.165.134/info.php 回车，就可以看到 PHP 的信息了。

#### 六、下载 WordPress

访问[Wordpress中文官方网站](cn.wordpress.org)

通过下面的命令下载中文或者英文版（二选一，推荐中文）：

* 下载中文版（也可以访问官文，直接下载,然后通过WinSCP直接上传）
> wget https://cn.wordpress.org/wordpress-4.9.4-zh_CN.zip
> 

* 下载英文版
> wget https://wordpress.org/latest.zip
> 

下载的文件位置位于Linux文件系统的 /root/ 下。


#### 七、解压
使用 unzip 来解压文件（unzip "对应的文件名"）：
* 解压中文版
> unzip wordpress-4.9.4-zh_CN.zip
> 
* 解压英文版
> unzip latest.zip
> 
#### 八、在 Mysql 中新建数据库
> mysql -u root -p
> 
通过上面的命令进入数据库，然后输入密码：password(第一次没有密码，直接Enter)

然后创建一个叫 wordpress 的数据库
> create database wordpress;（注意分号）
> 

#### 九、修改 wp-config.php 文件

通过WinSCP登录到Centos系统的文件管理系统中,查找wp-config-sample.php文件；

复制wp-config-sample.php中的文字到wp-config.php中。

*如果没有wp-config.php，在WinSCP的/var/www/html/中手动创建一个。*

按照下面的形式修改 wp-config.php 文件,

/** MySQL数据库名：wordpress */

define('DB_NAME', 'wordpress'); 

/** MySQL数据库用户名 :root*/

define('DB_USER', 'root'); 

/** MySQL数据库密码 :password*/

define('DB_PASSWORD', '');

/** MySQL主机（不用修改） */

define('DB_HOST', 'localhost');


#### 十、把文件复制到 /var/www/html 目录下

* 使用XShell命令
> cp -rf wordpress/* /var/www/html/

* 使用WinSCP可视化远程复制/移动（推荐使用）


#### 十一、测试
在浏览器中输入自己服务器的 ip (或者http://ip/wordpress)即可查看到自己主页。



