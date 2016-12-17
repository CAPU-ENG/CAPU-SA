### Migration
by Jack
2016.12.14

# Installation of php5.6 on Ubuntu 16.04 lts
```
sudo apt install mysql-server apache2 apache2-utils phpmyadmin
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt-get install php5.6 php5.6-mysql php-gettext php5.6-mbstring php-xdebug libapache2-mod-php5.6
sudo apt install php5.6-curl php5.6-xml
sudo a2dismod php7.0; sudo a2enmod php5.6; sudo service apache2 restart
sudo update-alternatives --set php /usr/bin/php5.6
```

# MySql settings
1. Import data; only excute once.
```
mysql -uroot -p < foo.sql
```

2. Change `sql_mode`
```
mysql > SET GLOBAL sql_mode=(SELECT REPLACE(@@sql_mode,'ONLY_FULL_GROUP_BY',''));
```
or add
```
[mysqld]  
sql_mode = "STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
```
to `/etc/mysql/my.cnf`

# Bbs src
```
git clone <git-src-url>
sudo mv CAPUBBS /var/www
ln -s /var/www/CAPUBBS .
```

# Apache minimal conf
```
<VirtualHost *:80> 
  ServerAdmin webmaster@localhost 
  DocumentRoot /var/www/CAPUBBS 
  ServerName chexie.net 
</VirtualHost> 
```
See also `vhost.conf.example`.

# HTTPS
Use [letsencypt](https://certbot.eff.org/#ubuntuxenial-apache)
```
sudo apt install letsencrypt python-letsencrypt-apache
sudo letsencypt --apache -d <FQDN>
```
