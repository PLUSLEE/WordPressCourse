# WordPress���ʹ

## ׼������

1. �����Ʒ�����
2. ���ذ�װXShell��Զ�����ӷ�������| ����ʹ����Ѷ����ҳ����¼�����ӷ�����
3. ���ذ�װWinSCP��Զ�����ӷ��������ӻ��ļ�����


### ʹ����Ѷ����ҳ��¼��������̨��������ʹ��XShell�������ȶ���
 
*��¼����*

![](http://p7dwnxgqw.bkt.clouddn.com/img/2018/%E8%85%BE%E8%AE%AF%E4%BA%91%E5%90%8E%E5%8F%B0.png)




## ������վ

�Ƽ�����ɵ��ʽ�̳̣��������̳��ж���Щ�ط��д���
>  https://www.cnblogs.com/DarrenChan/p/6622233.html

> https://www.cnblogs.com/flankershen/p/7476415.html

�����̳̽��ʹ��

****

## ��װ�������
### ����
* ����������ϵͳ��CentOS
*	���Ͳ����������Apache httpd
*	��̨���ԣ�PHP
*	���ݿ⣺MariaDB
*	ǰ�˿�ܣ�WordPress

### ����
#### һ����װApache
��װ Apache �ܼ򵥣�ֻ��Ҫ���ն�������������Ϳ����ˣ�
> sudo yum install httpd


sudo ����˼���� root �û���ʲô������yum install �����߰�װ��Ȼ������ yes ��ȷ�����ذ�װ�ˡ�

��װ���֮��������Ҫ��������
> sudo service httpd start
> 

���������������֮���ȱ��ż�����Ū������ֱ���������������������� ip ��ַ��Ӧ�þͿ��Կ��� Apache �Ļ�ӭҳ���ˡ�

>This page is used to test the operation of the Apache HTTP server after it has been installed��

������ ip ��ַ�Ѿ����������ˣ���ô��������������������Ҳ���Է����ˣ��ǲ��Ǻܿᣬ������ô�򵥣����Ǽ�����


#### ������װ MariaDB
��װ MariaDB
> yum install mariadb-server mariadb 

> systemctl start mariadb

ͨ�����������Ϳ��԰�װ�����������ݿ⣬��װ���ݿ��ʱ���ѯ����һЩ�򵥵����ã����� enter �� yes һ·������ OK �ˡ�

####  ������װ PHP �Լ���� PHP ���
�Ȱ�װ PHP
> sudo yum install php php-mysql
> 
��װ PHP ������
> yum install php-gd php-imap php-ldap php-odbc php-pear php-xml php-xmlrpc
> 

�˽����е� PHP ����Ļ�������ʹ����������������
> yum search php-
> 


#### �ġ�����Ĭ������ Apache �� Mysql ����(���� CentOS 6 �� 7 ʹ�õ��ǲ�ͬ��������)
ʹ�����������ѡ�񿪻����� Apache �� MariaDB:
> systemctl enable httpd

> systemctl enable mariadb
 
������ service --status-all ���鿴�����������Ƿ�������
 


#### �塢���� PHP �Ƿ�װ�ɹ�
����һ�� info.php �ļ���
> sudo nano /var/www/html/info.php

����༭ģʽ�����ļ���д������� PHP ���
```
<?php
    phpinfo();
?>
 ```

Ȼ��Ctrl+O ���棬Ctrl+X�˳���

������������� ��IP��ַ/info.php�������磺119.29.165.134/info.php �س����Ϳ��Կ��� PHP ����Ϣ�ˡ�

#### �������� WordPress

����[Wordpress���Ĺٷ���վ](cn.wordpress.org)

ͨ������������������Ļ���Ӣ�İ棨��ѡһ���Ƽ����ģ���

* �������İ棨Ҳ���Է��ʹ��ģ�ֱ������,Ȼ��ͨ��WinSCPֱ���ϴ���
> wget https://cn.wordpress.org/wordpress-4.9.4-zh_CN.zip
> 

* ����Ӣ�İ�
> wget https://wordpress.org/latest.zip
> 

���ص��ļ�λ��λ��Linux�ļ�ϵͳ�� /root/ �¡�


#### �ߡ���ѹ
ʹ�� unzip ����ѹ�ļ���unzip "��Ӧ���ļ���"����
* ��ѹ���İ�
> unzip wordpress-4.9.4-zh_CN.zip
> 
* ��ѹӢ�İ�
> unzip latest.zip
> 
#### �ˡ��� Mysql ���½����ݿ�
> mysql -u root -p
> 
ͨ�����������������ݿ⣬Ȼ���������룺password(��һ��û�����룬ֱ��Enter)

Ȼ�󴴽�һ���� wordpress �����ݿ�
> create database wordpress;��ע��ֺţ�
> 

#### �š��޸� wp-config.php �ļ�

ͨ��WinSCP��¼��Centosϵͳ���ļ�����ϵͳ��,����wp-config-sample.php�ļ���

����wp-config-sample.php�е����ֵ�wp-config.php�С�

*���û��wp-config.php����WinSCP��/var/www/html/���ֶ�����һ����*

�����������ʽ�޸� wp-config.php �ļ�,

/** MySQL���ݿ�����wordpress */

define('DB_NAME', 'wordpress'); 

/** MySQL���ݿ��û��� :root*/

define('DB_USER', 'root'); 

/** MySQL���ݿ����� :password*/

define('DB_PASSWORD', '');

/** MySQL�����������޸ģ� */

define('DB_HOST', 'localhost');


#### ʮ�����ļ����Ƶ� /var/www/html Ŀ¼��

* ʹ��XShell����
> cp -rf wordpress/* /var/www/html/

* ʹ��WinSCP���ӻ�Զ�̸���/�ƶ����Ƽ�ʹ�ã�


#### ʮһ������
��������������Լ��������� ip (����http://ip/wordpress)���ɲ鿴���Լ���ҳ��



