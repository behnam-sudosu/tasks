# caching server

## install
	sudo apt update && sudo apt install squid
	cd /etc/squid
		squid.conf
		port 3128
	memory and save in disk

# config file
    vim squid.conf
		cache_mem 256 MB
		maximum_object_size_in_memory 512 KB
		cache_dir ufs /var/spool/squid 100 16 256
			ufs ===>> file system squid
			/var/spool/squid ===>> directory to cache
			100 ===>> 100 MB
			16 ===>> directory
			256 ===>> 256 directory
		save file
		service squid restart or reload

# set browser
		open browser
			setting
			network setting
			manual proxy configuration
				192.168.1.100 port 3128
				check mark also use this proxy for HTTPS

# acl ===>> access control
	acl GOOGle dstdomain googl.com # deny only google.com
	acl GOOGle dstdomain .googl.com # deny google.com and all subdomains
	acl PRIVATE src 192.168.1.0/24

# http_access ===>> which acl deny or allow
	http_access deny !Safe_ports	
	http_access deny connect !SSL_ports ===>> only port 443
	http_access deny GOOGLE ===>> set rule
	http_access allow localhost manager
	http_access deny manager
	http_access allow localhost
	http_access deny all
save file
service squid restart

# user&pass
	apt install apache2-utils
	cd /usr/lib/squid
		basic_ncsa_auth
	vim /etc/squid.conf
		auth_param basic program /usr/lib/squid/basic_ncsa_auth /etc/squid/userfile
	htpasswd -c /etc/squid/userfile user1
		New password:
	htpasswd userfile user2
		New password:
	acl AUTHENTICATED proxy_auth REQUIERD
	http_access allow AUTHENTICATED
	save file
	service squid restart
	


