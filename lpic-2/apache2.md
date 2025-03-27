# apache2
	debian ===>> apache2
	config file ===>> /etc/apache2
	rhel ===>> httpd
	config file ===>> /etc/httpd
	
## module
	
## install    
	sudo apt update && sudo apt install apache2 ===>> debian
	sudo yum install httpd
	port is 80

## files    
	cd /etc/apache2/apche2.conf ===>> config file
	importan directory
		sites-available
		sites-enabled
		mods-available
		mods-enabled
	
    /var/log/apache2
		access.log
		error.log
	
    /etc/apache2/sites-enabled
		in this directory everything is linked
		the point to sites-available
	
    /etc/apache2/mods-enabled
		in this directory everything is linked
		the point to sites-available
	
    DocumentRoot /var/www/html
		index.html

# install moduls
## PHP
	sudo apt-cache search php | grep apache
	sudo apt update && sudo apt install libapache2-mod-php
	ls mods-available/ | grep php
		php7.4.conf
		php7.4.load
	ls mods-enabled/ | grep php
		php7.4.conf
		php7.4.load
## perl	
	sudo apt-cache search perl | grep apache
	sudo apt update && sudo apt install libapache2-mod-perl2
	ls mods-available/ | grep perl
		perl.load
	ls mods-enabled/ | grep php
		perl.load
	
# disable & enable
### first
	command
		disable
			a2enmod
			a2dismod ===>> a2dismod php7.4
			systemctl restart apache2
		ls mods-abailable/ | grep -i php
			php7.4.conf
			php7.4.load
		ls mods-abailable/ | grep -i php
			there is nothing
	
		enable
			a2enmod php7.4
			systemctl restart apache2		
		ls mods-available/ | grep -i php
			php7.4.conf
			php7.4.load
		ls mods-enabled/ | grep -i php
			php7.4.conf
			php7.4.load

### second
	unlink mods-enabled/	
	
# MPM
	prefork ===>> maybe have idle
	worker ===>> thread
	event
	apache2ctl ===>> you can stop, start, reload
	apache2ctl -V | grep -i mpm ===>> show which one is enabled
		server MPM:  prefork
	ls -l mods-enabled/ | grep mpm ===>> show which one is enabled
	
# authentication
	mkdir /var/www/html/protected
	cd /etc/apache2
	cat apache2.conf | grep -i include
		IncludeOptional sites-enabled/*.conf ===>> you must configure this file
	vim /var/www/html/protected/test.html
	cd /etc/apache2/sites-enabled
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
	htpasswd -c /etc/apache2/webpass user1 ===>> make user and password
	New password:
	htpasswd webpass user2 ===>> append user2
	New password 
	vim /etc/apache2/webpass ===>> make this
	service apache2 restart
	systemctl restart apache2
	apache2ctl restart
	
	auto index = on ===>> you can download
	/etc/apache2/apache2.conf

# redirect
	/var/www/html
	mkdir dir1
	mkdir redirect
		vim file.htm
			"redirect"
	vim /etc/apache2/sites-enabled/000-default.conf
		# redirect
		Redirect /dir1 /redirect
	systemctl restart apache2


# virtualhost
	in one server you can bring up some website
	/etc/apache2/sites-avilable
	vim site1.cong
		<VirtualHOst 192.168.1.100:80>
		ServerAdmin info@site1.com
		DocumentRoot /var/www/html/site1
		ServerName site1.com
		</VirtualHost>
	save file
	a2ensite site1 ===>> enable this site
	systemctl restart apache2
	vim site2.cong
		<VirtualHOst 192.168.1.200:80>
		ServerAdmin info@site2.com
		DocumentRoot /var/www/html/site2
		ServerName site2.com
		</VirtualHost>
	save file
	a2ensite site1 ===>> enable this site
	systemctl restart apache2



	