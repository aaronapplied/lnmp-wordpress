The Doc record the step how to deployed a personal web site.

相关介绍：
WordPress：是使用PHP语言开发的博客平台，用户可以在支持PHP和MySQL数据库的服务器上架设属于自己的网站，建立个人博客，也可以把 WordPress当作一个内容管理系统（CMS）来使用。WordPress有许多第三方开发的免费模板，安装方式简单易用
LNMP：Linux+Nginx+MySQL+PHP的组合的简称

The step how to deployed a personal web site on Centos 8 stream

1，下载LNMP自动化安装包来安装lnmp（安装时间很长45min左右，前提设置SSH回话超时时间）
LNMP一键安装包是一个用Linux Shell编写的可以为CentOS/RHEL/Fedora/Debian/Ubuntu/Raspbian/Deepin/Alibaba/Amazon/Mint/Oracle/Rocky/Alma/Kali/UOS/银河麒麟/openEuler/Anolis OS Linux VPS或独立主机安装LNMP(Nginx/MySQL/PHP)、LNMPA(Nginx/MySQL/PHP/Apache)、LAMP(Apache/MySQL/PHP)生产环境的Shell程序。
# wget https://soft.lnmp.com/lnmp/lnmp2.1-full.tar.gz
# tar zxf lnmp2.1-full.tar.gz
# cd lnmp2.1-ful
# ./install.sh lnmp 
安装过程版本选择mairadb-10:5  PHP-8.3以上

2.配置Nginx
访问http://ip，即可看到LNMP界面（云服务记得在安全组中提前开放80端口）

3.安装WordPress
WordPress官网：https://cn.wordpress.org/
WordPress是PHP语言写的，所以上一步安装LNMP就是为了保证WordPress的运行环境。
# wget https://cn.wordpress.org/latest-zh_CN.zip
# unzip latest-zh_CN.zip -d /home/wwwroot  # 解压到/home/wwwroot目录下

3.创建数据库
登录MySQL数据库，密码就是安装LNMP第②步时设置的密码，创建一个wordpress数据库。
# mysql>create database wordpress character set utf8 collate utf8_general_ci;

4.修改Nginx
# vim /usr/local/nginx/conf/nginx.conf
将80端口访问目录由”/home/wwwroot/default;”改为”/home/wwwroot/wordpress;”

修改完、保存后，记得重新加载Nginx配置文件：
#nginx -s reload


5.登录WordPress
WordPress后台
点击登录，也可以访问：http://ip/wp-admin/，输入账号密码登录即可。登录成功后，进入WordPress后台：

WordPress个人主页
输入http://ip进入个人主页.
