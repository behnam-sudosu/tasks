# network setting
	apt install net-tools
	
## temparary
### ifconfig
	ifconfig ===>> show ip
	ifconfig -a ===>> show all 
	ifconfig ens37 up ===>> bring interface up
	ifconfig ens37 down ===>> bring interface down
	ifconfig ens37 192.168.1.100 ===>> set ip static
	ifconfig ens37 netmask 255.255.255.0 ===>> set netmask
	ifconfig ens37 192.168.1.100 netmask 255.255.255.0
	ifconfig ens37 broadcast 192.168.1.100 ===>> set broadcast
	ifconfig ens37 hw ether aa:bb:cc:dd:ff:ee ===>> set mac address
	
	ifconfig ens37:0 192.168.1.10 ===>> set interface in a small
	mtu 1500 ===>> send packet in what size  (maximum transaction unit)
	ifconfig ens37 mtu 1450
	
### ip	
	ip address show ===>> show all ip
		ip addr sh
		ip a s
	ip a show wns37
	ip -br a
	ip -br -c a ===>> set color
	ip link set ens37 up
	ip link set ens37 down
	ip addr add 192.168.1.100/24 dev ens37
	ip addr del 192.168.1.100/24 dev ens37
	ip link set mtu 1700 dev ens37
	ip add 192.168.1.100/24 dev ens37:0
	ip del 192.168.1.100/24 dev ens37:0
	ip route show ===>> see all route
		ip ro sh
		ip r s
	ip route add 172.16.100.0/24 via 172.16.0.10
	ip route del 172.16.100.0/24 via 172.16.0.10
	ip route add default  via 172.16.0.10
	ip route del default  via 172.16.0.10
	
### route
	route ===>> show routing table
	route -n ==>> show destination
	route add -net 192.168.1.100/24 gw 192.168.1.110
	route del -net 192.168.1.100/24 gw 192.168.1.110
	route add default gw 192.168.1.1 ===>> change default
	route del default gw 192.168.1.1
	
### wireless
	apt install wireless-tools
	iwconfig
	arp ===>> show ip
	arp -a
	arp -v
	arp -s 192.168.1.110 aa:bb:cc:dd:ff ===>> add ip address
	arp -d aa:bb:cc:dd:ff
	
## permanent
	ubuntu ===>> vim /etc/netplan/*.yaml
	debian ===>> vim /etc/network/interfaces
	redhat ===? vim /etc/sysconfig/network-script/ifcfg-ens37
	
# port
### netstat
	netstat	===>> show all port
	netstat -a ===>> all
	netstat -t ===>> tcp
	netstat -u ===>> udp
	netstat -n ===>> number
	netstat -l ===>> list
	netstat -p ===>> protocol
	netstat -tuna

### ss
	ss -a ===>> all
	ss -t ===>> tcp
	ss -u ===>> udp
	ss -n ===>> number
	ss -l ===>> list
	ss -p ===>> number
	
## open port
	netcat
		server ===>> nc -l 5000 ===>> open port
		client telnet 192.168.1.100 5000 ===>> ip server
	for trobleshoot
	
## ping
	ping 8.8.8.8
	ping -c	===>> count
	ping -i 3 ===>> 3 second
	
## tcpdump
	tcpdump ===>> show all packet tcp in your system
	tcpdump -D ===>> show all interface
	tcpdump -i ens37 ===>> only packate interface ens37
	tcpdump -c 10 -i ens37 ===>> show only 10 the last
	tcpdump -w file.pcap -i ens37 ===>> w == save file 
	pcap file can read by wireshark too is perfosional
	tcp -r file.pcap ===>> read the file
	tcpdumo -i ens37 tcp ===>> show only tcp
	tcpdump -i ens37 port 80 ===>> show only port 80
	tcpdump -i ens37 src 192.1681.1.100 ===>> lisen on router
	tcpdump -i ens37 dst 192.168.10.0 ===>> dgkala ip who goes to it
	
## nmap
	nmap ===>> port scan
	apt install nmap
	nmap 192.168.1.100
	nmap google.com
	nmap 192.168.1.0-255 ===>> range ip
	nmap 192.168.1.100/24
	vim ips
		192.168.1.100
		192.168.1.110
	nmap -iL ips ===>> for run file
	nmap -p 22 192.168.1.100
	nmap -p 1-200 192.168.1.100 ===>> range port
	nmap -F ===>> fast scan
	nmap -p- 192.168.1.100 ===>> scan all port
	65535 ===>> we have port
		0-1024 ===>> system port
		1024-49151 ===>> user port
		49152-65535 ===>> private port
		
## name server	
	vim /etc/hosts
		192.168.1.200 google.com ===>> set DNS
	vim /etc/resolv.conf ===>> set DNS
		nameserver 8.8.8.8
	vim /etc/netplan/*.yaml
		namservers:
		  addresses: [8.8.8.8]

## troubleshoot
	apt install traceroute
	traceroute
	traceroute 8.8.8.8
	traceroute -i ens37 google.com
	traceroute google.com -w 2 ===>> wait 2 second
	tracepath 8.8.8.8
	mtr 8.8.8.8
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
