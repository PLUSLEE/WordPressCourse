# WordPress����-�趨�̶����Ӽ��趨֮��404�������취

* ���������WordPressϵͳĬ��ʹ�õ�"����"ģʽ

> http://ledplus.cc/wordpress/?p=123


����ģʽ���ŷǳ���࣬���Ǻ����p=123û��ʵ�ʺ��壬�������治�ܶ�����������и�Ч���������Ͼ���������Ϣ̫���ˣ�������վ����SEO�Ż�������

* �Ƽ�ʹ�� 

> ���ں�������    http://ledplus.cc/wordpress/2018/07/29/sample-post/

> �·ݺ�������    http://ledplus.cc/wordpress/2018/07/sample-post/

> ������         http://ledplus.cc/wordpress/sample-post/

����β�������а������������ƣ�����SEO�Ż���

------

## ѡ�зǡ����ء�ʱ����ĳ�����·�������404

��ʹ�õĲ��Ͳ����������Apache httpd������404�³�����һ��ʼ��С��ʱ����֪��������ʲô�����Ƿ����޸ĵ������ء�ģʽ���ܹ�����������ҳ��͵������Ҳ��û���ٸ��ġ�

���ٽ��Լ���ʼ���������������һ��SEO�Ż����󣬵ڶ��Ƿ���������ֻ��1C2G������վ�����ٶ��Ż���ʹ��WP-Super��Cache��Ҫ�Թ̶����ӽ������á�

----
����ԭ��**Apache������û�п���URL_Rewrite����**

����취������URL_Rewrite����
1. ʹ�ÿ���̨������XShell������WinSCP�����ӵ�������

2. **��wordpress��Ŀ¼�µ�.htaccessȨ�޽�������Ϊ777��ӵ�ж�дȨ��**

> ������wordpress���Ϳ���̨�޸Ĺ̶�����ʱ�����û�ж�дȨ�ޣ����Ϸ�����б�����ʾ


3. �л���httpd.conf���ڵ�λ�� /etc/httpd/conf/httpd.conf �ҵ�

> LoadModule foo_module modules/foo_rewrite.so
����������䣻����仰ȡ��ע��

4. ��httpd.conf�ļ����ҵ�</var/www/html����

> �޸�AllowOverride None �Ĳ�������ΪAll

5. ����Apache httpd������ֱ������������

����Apache httpd

> systemctl restart httpd


����������(����ʹ�ÿ���̨��������ť)

> reboot


----

�ο����£�

https://blog.csdn.net/wzl505/article/details/53337223