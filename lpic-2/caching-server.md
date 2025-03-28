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