### Migration
by Jack
2016年 12月 14日 星期三 11:14:48 CST

# install php5.6
```
sudo apt install mysql-server apache2 apache2-utils phpmyadmin
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt-get install php7.0 php5.6 php5.6-mysql php-gettext php5.6-mbstring php-xdebug libapache2-mod-php5.6 libapache2-mod-php7.0
sudo apt install php5.6-curl php5.6-xml
sudo a2dismod php7.0; sudo a2enmod php5.6; sudo service apache2 restart
sudo update-alternatives --set php /usr/bin/php5.6
```

# database
```
mysql -uroot -p < foo.sql
```

# Apache minimal conf
```
<VirtualHost *:80> 
   ServerAdmin webmaster@localhost 
   DocumentRoot /<path>/<to>/CAPUBBS 
   ServerName chexie.net 
   <Directory /> 
       Require all granted 
   </Directory> 
</VirtualHost> 
```

# HTTPS
TO-BE-DONE
