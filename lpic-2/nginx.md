# nginx
	debian ===>> nginx
	config file ===>> /etc/nginx
	rhel ===>> nginx
	config file ===>> /etc/nginx
	
## module

## install
	sudo apt update && sudo apt install nginx ===>> debian
	sudo install epel-release ===>> first install this repository
	sudo yum install nginx
	port is 80

## files
	cd /etc/nginx/nginx.conf ===>> config file
	importan directory
		sites-available
		sites-enabled
		modules-available
		modules-enabled

	/var/log/nginx
		access.log
		error.log

	/etc/nginx/sites-enabled
		in this directory everything is linked
		the point to sites-available
	
    /etc/nginx/modules-enabled
		in this directory everything is linked
		the point to sites-available
	
    DocumentRoot /var/www/html
		index.html



## install moduls
### PHP
	sudo apt-get install php8.1
	ls moduls-available/ | grep php	
	ls moduls-enabled/ | grep php
		

	
# disable & enable
### first
	command
		disable
			a2enmod
			a2dismod ===>> a2dismod php8.1
			systemctl restart nginx
		ls moduls-abailable/ | grep -i php
		
		ls moduls-abailable/ | grep -i php
			there is nothing
	
		enable
			a2enmod php8.1
			systemctl restart nginx		
		ls moduls-available/ | grep -i php
			
		ls mods-enabled/ | grep -i php
			

### second
	unlink moduls-enabled/	
	
# MPM
	prefork ===>> maybe have idle
	worker ===>> thread
	event
	ls -l moduls-enabled/ | grep mpm ===>> show which one is enabled
	
# authentication
	mkdir /var/www/html/protected
	cd /etc/nginx
	cat nginx.conf | grep -i include
		IncludeOptional sites-enabled/*.conf ===>> you must configure this file
	vim /var/www/html/protected/test.html
	cd /etc/nginx/sites-enabled
	vim 000-default.conf
		DocumentRoot /var/www/html
		# password protected
		<Directory /var/www/html/protected>
			AuthType Basic
			AuthName "This is protected directory"
			AuthUserFile /etc/apache2/webpass
			Require valid-user
		</Directory>
	save file
	sudo apt install apache2-utils
	htpasswd -c /etc/nginx/webpass user1 ===>> make user and password
	New password:
	htpasswd webpass user2 ===>> append user2
	New password 
	vim /etc/nginx/webpass ===>> make this
	service nginx restart
	systemctl restart nginx
	


	