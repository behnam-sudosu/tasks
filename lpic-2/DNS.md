# DNS
	DNS ===>> Domain Name Service
	bind DNS
	power DNS
	microsoft DNS
	bg DNS
	mask DNS
	
	DNS local
	DNS server
	cach server
	
	/etc/hosts
	/etc/resolv.conf
	/etc/netplan/*.yaml ===>> ubuntu
	
# command
## nslookup
	nslookup google.com
	nslookup 216.239.38.120
	nslokkup -query=a google.com
	nslookup -query=mx google.com
	nslookup -query=nx google.com
	nslookup google.com 8.8.8.8
	nslookup -debug google.com
## host
	host google.com
	host -t ns yahoo.com
	host -t mx yahoo.com
	host google.com 8.8.8.8
## dig
	dig google.com
	dig google.com mx
	dig google.com +short
	dig @8.8.8.8 google.com
	dig google.com +trace
	
# record
	A record or AAA record ===>> name point to ip
	syname record ===>> point name to another name
	mx record ===>> mail exchange
	ns record ===>> name server record
	
# DNS server
	apt install bind9
	apt install bind9utils
	cd /etc/bind
	vim name.conf
		you can add include new file or your config file
	vim name.conf.options
		forwarders{
		8.8.8.8
		}
		recursion yes; ===>> cash server
		forward 0nly; ===>> dosn't cach
	systemctl restart bind9.service
	dig @localhost google.com
	you can run DNS as cach or forward
	systemctl status bind9.service
	you can use coreDNS



    