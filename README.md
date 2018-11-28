# LAMP-autoinstall
CentOS + Apache2.4 + PHP7 + MySQL8 + phpMyAdmin 一键安装

# 安装指南：
使用root连接服务器
```bash
cd ~
yum install -y git
git clone https://github.com/pzn2513/LAMP.git
chown 700 -R LAMP/bin
LAMP/bin/lamp-install
```
等待安装



MySQL--获取临时登录密码，修改密码
```bash
- grep 'temporary password' /var/log/mysqld.log
- alter user 'root'@'localhost' identified by 'Abc.123456';

其他操作
- show variables like 'character%';
- select host,user,plugin,authentication_string from mysql.user;
- use mysql;
- insert user VALUES ('localhost', 'pzn', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', '', '', '', '', '0', '0', '0', '0', 'mysql_native_password', '*84AAC12F54AB666ECFC2A83C676908C8BBC381B1', 'N', '2018-04-21 11:25:16', null, 'N', 'Y', 'Y', null, null);
- FLUSH PRIVILEGES;
```
MySQL8的配置变化比较大，如果无法成功配置可以寻求帮助，见[Bugs & Issues](#bugs--issues)


Default Location
================
| Apache Location            | Path                                             |
|----------------------------|--------------------------------------------------|
| Install Prefix             | /usr/local/apache24                              |
| Web root location          | /usr/local/apache24/htdocs                       |
| Main Configuration File    | /usr/local/apache24/conf/httpd.conf              |
| Virtual Host conf          | /usr/local/apache24/conf/extra/httpd-vhosts.conf |
| SSL Host conf              | /usr/local/apache24/conf/extra/httpd-vhosts.conf |

| phpMyAdmin Location        | Path                                             |
|----------------------------|--------------------------------------------------|
| Installation location      | /usr/local/apache24/htdocs/phpMySQLAdmin-secret  |

| PHP Location               | Path                                             |
|----------------------------|--------------------------------------------------|
| Install Prefix             | /usr/local/php                                   |
| Configuration File         | /usr/local/php/etc/php.ini                       |

| MySQL Location             | Path                                             |
|----------------------------|--------------------------------------------------|
| Install Prefix             | /usr/local/mysql                                 |
| Data Location              | /usr/local/mysql/data                            |
| my.cnf Configuration File  | /etc/my.cnf                                      |


Process Management
==================
| Process     | Command                                                         |
|-------------|-----------------------------------------------------------------|
| Apache      | /usr/local/apache24/bin/apachectl (start\|stop\|status\|restart)|
| MySQL       | systemctl (start\|stop\|status\|restart) mysqld.service         |

lamp Command
============
| Command        | Description                                                                         |
|----------------|-------------------------------------------------------------------------------------|
| lamp-init      | 初始化各个配置文件                                                                    |
| addvhost (site)| 添加vhost，在/home下创建site目录                                                      |
| addssl (site)  | 添加ssl，在/home下创建site目录，需要在/usr/local/apache24/cert/(site)配置证书文件       |
| addboth (site) | 添加vhost和ssl，在/home下创建site目录，需要在/usr/local/apache24/cert/(site)配置证书文件|

Bugs & Issues
=============
Please feel free to report any bugs or issues to us, email to: pznforwork@outlook.com or [issues](https://github.com/pzn2513/LAMP-autoinstall/issues) on Github.


License
=======
Copyright (C) 2016 - 2018 PZN

Licensed under the [GPLv3](https://github.com/pzn2513/LICENSE/blob/master/README.md) License.
