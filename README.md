# LAMP-autoinstall
CentOS + Apache2.4 + PHP7 + MySQL8 + phpMyAdmin 一键安装

使用指南：



获取临时登录密码，修改权限
- grep 'temporary password' /var/log/mysqld.log
- alter user 'root'@'localhost' identified by 'Abc.123456';
- show variables like 'character%';
- select host,user,plugin,authentication_string from mysql.user;
- use mysql;insert user VALUES ('localhost', 'pzn', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', '', '', '', '', '0', '0', '0', '0', 'mysql_native_password', '*84AAC12F54AB666ECFC2A83C676908C8BBC381B1', 'N', '2018-04-21 11:25:16', null, 'N', 'Y', 'Y', null, null);
- FLUSH PRIVILEGES;
