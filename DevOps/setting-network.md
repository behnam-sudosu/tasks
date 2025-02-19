# setting-network

    ip -br a ===>> show your ip

## permanent
### ubuntu
    vim /etc/netplan/*.yamel
### centos, rocky, alma
    vim /etc/sysconfig/network-script/ifcfg-ens37
### deb
    vim /etc/network/interfaces


#### install net-tools
    sudo apt update
    sudo apt install net-tools

## temporary

### ifconfig
    ifconfig ===>> show your interfaces
    ifconfig -a ===>> show all interfaces
    ifconfig ens37 192.168.80.100
    ifconfig ens37 netmask 255.255.255.0
    ifconfig ens37 192.168.80.100 netmask 255.255.255.0

### ip address
    ip address show
    ip addr sh
    ip ad sh
    ip a s
    ip a
    ip address add 192.168.200.200/24 dev ens37
    ip address del 192.168.200.200/24 dev ens37
    ip link show
    ip link set ens37 down
    ip link set ens37 up

### ip route
    ip route show
    ip route list
    ip route
    ip ro sh
    ip r s
    ip r
    ip toute add 12.0.0.0/8 via 192.168.1.100 dev ens37
    ip toute del 12.0.0.0/8 via 192.168.1.100 dev ens37
    
### route
    route
    route -n
    route add default gw 192.168.1.100 ens37
    route delete default gw 192.168.1.100 ens37
    route add 12.0.0.0/8 via 192.168.1.100 dev ens37




