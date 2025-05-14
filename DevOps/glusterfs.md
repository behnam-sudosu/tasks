# glustrefs

## use two way
	replicated (HA) ===>> if you have 3 server 1T use 3T
	distributed (scale) ===>> if you have 100G storage you you can use 150G
	client and server conection NFS, Gluster
	
## server side
    <!-- install repository -->
    sudo apt update
    sudo apt install software-properties-common
	sudoadd-apt-repository ppa:gluster/glusterfs-7
	sudo apt install glusterfs-server
	

	sudo apt update
	sudo apt install glusterfs-server
	
## client side