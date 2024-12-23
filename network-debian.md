<!-- network setting -->
# config network 
### set ip static for debian
1.
    cd /etc/network

2.
    vim interfaces
        # The loopback network interface
        auto lo
        iface lo inet loopback
        
        # The primary network interface
        auto ens36
        iface ens36  inet static
                address 192.168.1.100/24
                netmask 255.255.255.0
                gateway 192.168.1.1
                dns-nameservers 8.8.8.8
    
    save the file
3.
    sudo systemctl restart networking.service

### set nameserver

    cd /etc
    vim resolv.conf
        nameserver 8.8.8.8
        nameserver 4.2.2.4
    save the file
    