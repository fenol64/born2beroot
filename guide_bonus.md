# Bonus part

what you need to do to complete the bonus part

1. install utils
2. install and configure lighttpd
3. install and configure php
4. install and configure mariadb
5. install and configure wordpress
6. install and configure a service of your choice (ex: adminer, phpmyadmin, ftps, ssh, etc.)

### install dependecies

```bash
    apt-get install -y lighttpd mariadb-server wget php php-cgi php-cli php-fpm php-curl php-gd php-mysql php-mbstring zip unzip
```

### delete apache2

```bash
    apt-get purge apache2 apache2-utils apache2.2-bin apache2-common
    # remove unused packages
    apt-get autoremove
    # remove apache2 config files
    rm -rf /etc/apache2
```

### install and configure lighttpd with php

```bash
    # enable port 80
    ufw allow 80
    # check if port is open
    ufw status
    # start lighttpd service on boot
    systemctl enable lighttpd
    # start lighttpd service
    systemctl start lighttpd

    # enable php and cgi modules
    lightty-enable-mod fastcgi fastcgi-php
    # restart lighttpd
    service lighttpd restart
```

check your ip address with `hostname -I` and after that you can check if lighttpd is working by going to your VM ip address in your browser (ex: http://{IP})

### install and configure mariadb

```bash
    # secure mariadb installation
    mysql_secure_installation
    # start mariadb
    mariadb
```

2. create mariadb user

```sql
    CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
    GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' WITH GRANT OPTION;
    FLUSH PRIVILEGES;
```

3. create database

```sql
    CREATE DATABASE wordpress;
```

4. exit mariadb

```sql
    exit
```

### install and configure wordpress

```bash
    # download wordpress
    wget wget https://wordpress.org/latest.zip
    # extract wordpress
    unzip latest.zip
    # move wordpress to /var/www/html
    mv wordpress /var/www/html
    # change wordpress owner
    chown -R www-data:www-data /var/www/html/wordpress
    # change wordpress permissions
    chmod -R 755 /var/www/html/wordpress
```

after that you can check if wordpress is working by going to your VM ip address in your browser (ex: http://{IP}/wordpress)

5. configure wordpress if needed (wp makes this step.)

```bash
    # create wordpress config file
    cd /var/www/html/wordpress
    mv wp-config-sample.php wp-config.php
    # edit wordpress config file
    vim wp-config.php
```
