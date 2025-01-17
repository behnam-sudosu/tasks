<!-- network setting -->
# config network Centos
### set ip static for centos
1.

    vim /etc/sysconfig/network-scripts/ifcfg-ens37

2.

    TYPE=Ethernet
    BOOTPROTO=none
    IPADDR=192.168.2.203
    PREFIX=24
    GATEWAY=192.168.2.254
    DNS1=192.168.2.254
    DNS2=8.8.8.8
    DNS3=8.8.4.4
    DEFROUTE=yes
    IPV4_FAILURE_FATAL=no
    IPV6INIT=no
    NAME=eth0
    DEVICE=eth0
    ONBOOT=yes
### save the file

3.

    systemctl restart network










