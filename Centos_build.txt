#!/bin/bash

# yum update -y --exclude=kernel

# Tools
yum install -y nano git unzip screen

#apache
yum insall -y httpd http-devel httpd-tools
chkconfig --add httpd
chkconfig httpd on 
service httpd stop 

rm -rf /var/www/html
ln -s /vagrant /var/www/html

service httpd start

# PHP
yum install -y php php-cli php-common php-devel php-mysql

#mysql
yum install -y mysql mysql-server mysql-devel 
chkconfig --add mysqld
chkconfig mysqld on 

service mysqld start 

mysql -u root -e "SHOW DATABASES";

# Download Starter Content

service httpd restart

