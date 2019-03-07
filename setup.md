# Setup LAMP, on AWS EC2 (Ubuntu 18.04)

_To follow this, you should have basic understanding of Linux commands as well as AWS instance creation. If so, you can easily setup LAMP on any Ubuntu based EC2 instance, by following steps below..._

--------

First step connect to SSH, 
> ssh -i KEY-FILE.pem ubuntu@<PUBLIC-DNS / IP>

Once you're in console you can start by following steps to setup lamp

> `sudo apt update`

> `sudo apt install -y apache2`

> `(optional) sudo apt install -y curl`

> `(optional) sudo apt install -y composer`

> `sudo apt install -y mysql-server`

> `sudo apt update`

## Setup PHP (PHP7.2 is available ubuntu 18.04)
> `sudo apt-get install php -y`

> `sudo apt install -y libapache2-mod-php php-mysql`

## Setup PHPMyAdmin
> `sudo apt install -y phpmyadmin php-mbstring php-gettext`

> `sudo phpenmod mbstring`

## Setup root user password
> `sudo mysql`

> - ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'SomePassWord';

> - FLUSH PRIVILEGES;

## Create new mysql user and allow access to that user

> `mysql -u root -p` enter root password if any, if this does not work, just enter `sudo mysql`

> CREATE USER 'aws_dba'@'localhost' IDENTIFIED BY 'SomePassword';

> CREATE USER 'aws_dba'@'%' IDENTIFIED BY 'SomePassword';

> GRANT ALL ON *.* TO 'aws_dba'@'localhost';

> GRANT ALL ON *.* TO 'aws_dba'@'%';

> FLUSH PRIVILEGES; 

> EXIT;
