# WEB SOLUTION WITH WORDPRESS





### MOUNT INSTANCE
![Mount Instance](/images/mounts-configuration-successful%20project6.PNG)

## SETUP WORDPRESS
### INSTALL APACHE AND PHP
* sudo yum -y update
* sudo yum -y install wget httpd php php-mysqlnd php-fpm php-json
### START APACHE
* sudo systemctl enable httpd
* sudo systemctl start httpd

### INSTALL PHP DEPENDENCIES
* sudo yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
* sudo yum install yum-utils http://rpms.remirepo.net/enterprise/remi-release-8.rpm
* sudo yum module list php
* sudo yum module reset php
* sudo yum module enable php:remi-7.4
* sudo yum install php php-opcache php-gd php-curl php-mysqlnd
* sudo systemctl start php-fpm
* sudo systemctl enable php-fpm
setsebool -P httpd_execmem 1
### Restart Apache
* sudo systemctl restart httpd

### DOWNLOAD WORDPRESS AND COPY ADDRESS TO var/www/html

 * mkdir wordpress
 * cd   wordpress
 * sudo wget http://wordpress.org/latest.tar.gz
 * sudo tar xzvf latest.tar.gz
 * sudo rm -rf latest.tar.gz
 * cp wordpress/ 
 wp-config-sample.php wordpress/wp-config.php
 * cp -R wordpress /var/www/html/
### CONFIGURE SELinux POLICIES

 * sudo chown -R apache:apache /var/www/html/wordpress
 * sudo chcon -t httpd_sys_rw_content_t /var/www/html/wordpress -R
 * sudo setsebool -P httpd_can_network_connect=1
## MY SQL INSTALLED
### Install MySQL on DB Server
* sudo yum update
* sudo yum install mysql-server

* sudo systemctl start mysqld
* sudo systemctl enable mysqld

![MY SQL](/images/successfully_connected_to_mysqlserver.PNG)
## WORDPRESS
* http://< Web-Server-Public-IP-Address >/wordpress/

![WORDPRESS](/images/wordpress-project6.PNG)
## WORD PRESS CONNECTED

![WORDPRESS WELCOME PAGE](/images/welcome-wordpress_project6.PNG)
