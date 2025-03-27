# nginx
	debian ===>> nginx
	config file ===>> /etc/nginx
	rhel ===>> nginx
	config file ===>> /etc/nginx
	nginx -t ===>> check config file
	nginx -? ===>> help
	
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
	

# redirect
	/var/www/html
	mkdir dir1
	mkdir redirect
		vim file.htm
			"redirect"
	vim /etc/nginx/sites-enabled/000-default.conf
		# redirect
		Redirect /dir1 /redirect
	systemctl restart nginx


# virtualhost
	in one server you can bring up some website
	/etc/nginx/sites-avilable
	vim site1.cong
		<VirtualHOst 192.168.1.100:80>
		ServerAdmin info@site1.com
		DocumentRoot /var/www/html/site1
		ServerName site1.com
		</VirtualHost>
	save file
	make link to site-enabled
	systemctl restart nginx
	vim site2.cong
		<VirtualHOst 192.168.1.200:80>
		ServerAdmin info@site2.com
		DocumentRoot /var/www/html/site2
		ServerName site2.com
		</VirtualHost>
	save file
	make link to site-enabled
	systemctl restart nginx
	
# proxy pass
	/etc/nginx/
	proxy_params
	cd sites-available
	vim example.com
		server {
			listen 80;
			server_name example.com;
			location /{
			proxy_pass https://yahoo.com;
			}
		}
	save file
	vim /etc/hosts
		192.168.1.199 example.com
		127.0.0.1 example.com
	save file
	ln -s /sites-available/example.com ../sites-enabled
	nginx -t
	service nginx restart or reload
	
	see site in terminal
		sudo apt install elinks
		elinks http://example.com





