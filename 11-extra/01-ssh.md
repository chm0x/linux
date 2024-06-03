# SSH

## VIRTUALBOX

To connect, needs: 
* Required VirtualBox settings. 
* Required Linux Software 

## Install SSH 
Ubuntu: 
```
$ sudo apt install openssh-server openssh-client
```

Red Hat: 
```
sudo yum install openssh-server openssh-client
```


## INSTALLING NGINX, MYSQL, PHP, AND WORDPRESS ON UBUNTU 

**NGINX**
```
$ sudo apt install nginx 
$ systemctl status nginx
$ sudo systemctl enable nginx

$ curl http://127.0.0.1
$ curl http://localhost
```

**MYSQL**
```
$ sudo apt install -y mysql-server 
$ systemctl status mysql

# Create a database
$ sudo mysqladmin create wordpress_db 

# Log in
$ sudo mysql

# Create a user
mysql> CREATE USER wordpress_user@localhost IDENTIFIED BY 'passwd';
mysql> GRANT ALL ON wordpress_db.* TO wordpress_user@localhost;
mysql> FLUSH PRIVILEGES;
mysql> SET PASSWORD FOR wordpress_user@localhost = 'another_pwd';

# Conect Mysql With user and Database
$ mysql -u wordpress_user -p wordpress_db
```

**PHP**

phpfpm stand for 'PHP Fast CGI Process Manager'

```
$ sudo apt install -y php-fpm php-mysql php-curl php-mbstring php-imagick php-xml php-zip

$ systemctl status php
$ systemctl status php7.4-fpm.service

$ cd /etc/nginx/sites-available
$ sudo cp default default.bak
$ sudo nano default
```

Content, just like APACHE conf. 
```
index index.php index.html index.htm index.nginx-debian.html;

try_files $uri $uri/ /index.php$is_args$args;
```
Course lesson 74 if you search.


```
$ sudo nginx -t
$ sudo systemctl reload nginx

$ tar xvf wordpress-5.6.tar.gz
$ sudo mv wordpress/* /var/www/html/
$ sudo chown -R www-data:www-data /var/html/


```