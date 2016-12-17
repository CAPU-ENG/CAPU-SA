### Migration
by Jack
2016.12.14

# Installation of php5.6 on Ubuntu 16.04 lts
```
sudo apt install mysql-server apache2 apache2-utils phpmyadmin
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt-get install php5.6 php5.6-gd php5.6-fpm php5.6-mysql php-gettext php5.6-mbstring php-xdebug libapache2-mod-php5.6
sudo apt install php5.6-curl php5.6-xml
sudo a2dismod php7.0
sudo a2enmod php5.6
sudo a2enmod sudo a2enmod proxy_fcgi setenvif
sudo a2enconf php5.6-fpm
sudo service apache2 restart
sudo update-alternatives --set php /usr/bin/php5.6
sudo service php5.6-fpm restart
```

# MySql settings
Import data; only excute once.
```
mysql -uroot -p < foo.sql
```

# CAPUBBS src
```
git clone <git-src-url>
sudo mv CAPUBBS /var/www
ln -s /var/www/CAPUBBS
sudo chgrp www-date CAPUBBS/bbs/images CAPUBBS/attachment
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
