nfs setting

1.

    vim /etc/netplan/*.yaml
    <!-- set IP static -->
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
    sudo netplan try

2.

    change hostname

    <!-- first use this command -->
        hostnamectl set-hostname srv1
    <!-- second editing this file  -->
        vim /etc/hosts or vim /etc/hostname

3.

server side
    <!-- ip server is 192.168.80.100 -->
    sudo apt install nfs-kernel-server
    sudo apt install nfs-common
    mkdir /mnt/nfs
    chown nobody:nogroup /mnt/nfs
    chmod 777 /mnt/nfs
    vim /etc/exports
        /mnt/master 192.168.80.0/24(rw,sync,no_subtree_check)
        <!-- you can choose range ip for example 80 -->
    exportfs -r # this is a command
    exportfs -a # this is a command
    sudo systemctl restart nfs-kernel-server.service

4.
client side
    sudo apt install nfs-command
    mkdir /mnt/nfs
    chown nobody:nogroup /mnt/nfs
    chmod 777 /mnt/nfs
    mount 192.168.80.100:/mnt/nfs /mnt/nfs

df -h

5.
permanent 
    vim /etc/fstab
        192.168.80.100:/mnt/nfs /mnt/nfs nfs defaults 0 0
    mount -a
