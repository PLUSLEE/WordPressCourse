# WordPress博客-设定固定链接及设定之后404问题解决办法

* 情况描述：WordPress系统默认使用的"朴素"模式

> http://ledplus.cc/wordpress/?p=123


这种模式看着非常简洁，但是后面的p=123没有实际含义，搜索引擎不能对这个东西进行高效的搜索，毕竟包含的信息太少了，对于网站进行SEO优化不利。

* 推荐使用 

> 日期和名称型    http://ledplus.cc/wordpress/2018/07/29/sample-post/

> 月份和名称型    http://ledplus.cc/wordpress/2018/07/sample-post/

> 文章名         http://ledplus.cc/wordpress/sample-post/

这样尾部链接中包含了文章名称，便于SEO优化。

------

## 选中非“朴素”时，打开某个文章发现文章404

我使用的博客部署服务器是Apache httpd，出现404事出有因。一开始是小白时，不知道发生了什么，但是发现修改到“朴素”模式就能够正常访问内页，偷了懒，也就没有再更改。

而促进自己开始更改这个东西，第一是SEO优化需求，第二是服务器配置只有1C2G，对网站进行速度优化，使用WP-Super—Cache需要对固定链接进行设置。

----
问题原因：**Apache服务器没有开启URL_Rewrite功能**

解决办法：开启URL_Rewrite功能
1. 使用控制台（或者XShell，或者WinSCP）连接到服务器

2. **将wordpress根目录下的.htaccess权限进行设置为777，拥有读写权限**

> 当你在wordpress博客控制台修改固定链接时，如果没有读写权限，最上方会进行报错提示


3. 切换到httpd.conf所在的位置 /etc/httpd/conf/httpd.conf 找到

> LoadModule foo_module modules/foo_rewrite.so
或者类似语句；将这句话取消注释

4. 在httpd.conf文件中找到</var/www/html字样

> 修改AllowOverride None 的参数设置为All

5. 重启Apache httpd；或者直接重启服务器

重启Apache httpd

> systemctl restart httpd


重启服务器(或者使用控制台的重启按钮)

> reboot


----

参考文章：

https://blog.csdn.net/wzl505/article/details/53337223