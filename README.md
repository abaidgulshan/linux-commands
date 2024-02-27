# linux-commands
My Linux Commands 

## Install Nginx 1.9 to ubuntu Manual way 
```
 echo "deb http://nginx.org/packages/mainline/ubuntu/ trusty nginx" | sudo tee -a /etc/apt/sources.list
 echo "deb-src http://nginx.org/packages/mainline/ubuntu/ trusty nginx" | sudo tee -a /etc/apt/sources.list
 cat /etc/apt/sources.list
 wget -q -O- http://nginx.org/keys/nginx_signing.key | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install nginx -y
 nginx -v
```



* `history | awk '!($1="")'` --- When I dont need numbering with my history
* Folder permissions
```
sudo chown -R www-data .
sudo chgrp -R www-data .
sudo chmod -R g+rwxs .
```

### Generate Paid SSL on Apache 
#### Generate CSR 
* `openssl req -new -newkey rsa:2048 -nodes -keyout abaidgulshan.com.key -out abaidgulshan.com.csr`
### PHPmyadmin Security tips

#### Add htaccess

* `sudo apt-get install apache2-utils` --- install apache utils 
* `sudo vi /etc/phpmyadmin/apache.conf` -- and add following lines
```
<Directory /usr/share/phpmyadmin>
        Options FollowSymLinks
        DirectoryIndex index.php
        AllowOverride All
```
* `sudo vi /usr/share/phpmyadmin/.htaccess` --- now create the .htaccess file
```
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/apache2/.phpmyadmin.htpasswd
Require valid-user
```
* `sudo htpasswd -c /etc/apache2/.phpmyadmin.htpasswd username` --- add username and password after enter
* `sudo vi /etc/phpmyadmin/apache.conf` --- change the alias to access the phpmyadmin
```
Alias /phpmyadmin7iuhyY /usr/share/phpmyadmin
```
* `sudo service apache2 restart`

### Cron Jobs examples 

Ubuntu 14.04 server crons jobs 
* Open the crontab `vi /etc/crontab`
* cron runs every month once `01 1    1 * *   root php /command`

### Github Submodules

* `git clone git@github.com:test/buddy-works-test.git`
* `git submodule add git@github.com:test/buddy-works-embed-test.git buddy-works-embed-test`
* `git add --all && git commit -am "add submodule "`
* `git push origin master`
