# Zabbix Installation

> # apt-get install php7.0-bcmath php7.0-xml php7.0-mbstring

> $ wget http://repo.zabbix.com/zabbix/3.2/ubuntu/pool/main/z/zabbix-release/zabbix-release_3.2-1+xenial_all.deb

> # dpkg -i zabbix-release_3.2-1+xenial_all.deb

> # apt-get update

> # apt-get install zabbix-server-mysql zabbix-frontend-php

> # apt-get install zabbix-agent

# Configuring Mysql for Zabbix 

> $ mysql -uroot -p

> mysql> CREATE DATABASE zabbix CHARACTER SET utf8 COLLATE utf8_bin;

> mysql> GRANT ALL PRIVILEGES ON zabbix.* TO zabbix@localhost IDENTIFIED BY 'usr_strong_pwd'

> mysql> EXIT;

> apt install zabbix-server-mysql

> # zcat /usr/share/doc/zabbix-server-mysql/create.sql.gz | mysql -uzabbix -p zabbix

> # $EDITOR /etc/zabbix/zabbix_server.conf

> Alter DBPassword and DBHost in this file.

# Configuring PHP

> $EDITOR /etc/zabbix/apache.conf

* In this file edit:

> <IfModule mod_php7.c>
>    php_value max_execution_time 300
>    php_value memory_limit 128M
>    php_value post_max_size 16M
>    php_value upload_max_filesize 2M
>    php_value max_input_time 300
>    php_value always_populate_raw_post_data -1
>    php_value date.timezone Europe/Rome
> </IfModule>

> # systemctl restart apache2
> # systemctl start zabbix-server
> # systemctl enable zabbix-server

> # systemctl status zabbix-server

# Acess Zabbix Server

> http://localhost/zabbix

# Credits

* https://www.unixmen.com/monitoring-server-install-zabbix-ubuntu-16-04/

* And Rodrigo Leal
