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