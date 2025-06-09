# config network Ubuntu
### set ip static for ubuntu
1.
    cd /etc/netplan/


2.
    vim *.yaml

        # Let NetworkManager manage all devices on this system
        network:
            version: 2
            rendere: NetworkManager
            etherents:
            enp0s25:
                dhcp4: false 
                addresses:
                - 192.168.1.100/24
                gateway4: 192.168.1.1
    save the file

3.
    sudo netplan try or sudo netplan apply

### set nameservers

    cd /etc
    <!-- resolv.conf is a link in ubuntu 22.4 -->
    <!-- remove resolv.conf-->
    sudo rm -rf resolv.conf
    touch /etc/resolv.conf
    vim resolv.conf
        nameserver 8.8.8.8
        nameserver 4.2.2.4
    save the file

#### also you can add nameserver to /etc/netplan/*.yaml too


## route
#### you can change gateway4 to this
    routes:
        - to: default
          via: 192.168.0.1

