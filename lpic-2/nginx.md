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