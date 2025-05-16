# glustrefs

#### use two way
	replicated (HA) ===>> if you have 3 server 1T use 3T
	distributed (scale) ===>> if you have 100G storage you you can use 150G
	client and server conection NFS, Gluster

# replicated
## server side	
	
## config server
### set ip
	vim /etc/netplan/*.yaml
		# This is the metwork config written by 'behnam'
		network:
		  ethernets:
		    ens33:
		    	dhcp4: false
		    	addresses:
		    	 - 192.168.1.12/24
		    	gateway4: 192.168.80.2
		  version: 2
	  save file
	  set two interface
	  
### set hostname
	vim /etc/hosts ===>> change hosts to gl1
	sudo hostnamectl set-hostname gl1

### set LVM
	pvcreate /dev/sdb
	vgcreate glustervg /dev/sdb
	lvcreate -l 100%VG -n glusterlv glustervg
	mkfs.ext4 /dev/glustervg/glusterlv
	blkid /dev/glustervg/glusterlv ===>> find uuid
	mkdir /mnt/glustervolume
	ls -l dev/glustervg/glusterlv
	ls -l /dev/disk/by-uuid ===>> find uuid
	vim /etc/fstab
		/dev/glustervg/glusterlv /mnt/glustervolume ext4 defaults 00
		/dev/disk/by-uuid/e720966e-2b0b-4814-8820-4e42aca93e1c /mnt/glustervolume ext4 defaults 0 0
	mount -a
	df -h

### install package
	sudo apt update
	sudo apt install software-properties-common
	sudo apt install glusterfs-server
	
	sudo systemctl status glusted
	sudo systemctl enable glusted
	sudo systemctl start glusted
	
### set config
	vim /etc/hosts
		192.168.1.11 gl1
		192.168.1.12 gl2
		192.168.1.13 gl3

### commands
	only write this command on one server for example gl1 
	gluster peer brobe gl2
	gluster peer brobe gl3
	gluster peer status
	gluster pool list
	
### make pool
	mkdir /mnt/glustervolume/vol1
	gluster volume create vol1 replica 3 gl1:/mnt/glustervolume/vol1 gl2:/mnt/glustervolume/vol1 gl3:/mnt/glustervolume/vol1
	gluster volume start vol1
	gluster volume status
	
# client side


### install package
	sudo apt update
	sudo apt install glusterfs-server
	or
	sudo apt install glusterfs-client
	
### set config
	vim /etc/hosts
		192.168.1.11 gl1
		192.168.1.12 gl2
		192.168.1.13 gl3
	mkdir /mnt/vol1
	echo "gl3:/mn/glusterfs/vol1 /mnt/vol1 glusterfs defaults 00" >> /etc/fstab
	mount -a
	sudo systemctl daeman-reload
	df -h

# Delete glusterfs
	gluster volume list
	gluster volume info vol1
	gluster volume status

## client side
	umount /mnt/vol1

## server side
	gluster volume stop vol1
	gluster volume info vol1
	gluster volume delete vol1
	gluster volume list
	vim /etc/fstab
		comment line

# distributed
	
## server side
	gluster volume list
	gluster volume status
	gluster volume create vol2 g1:/glustervolume/vol2 g2:/glustervolume/vol2 g3:/glustervolume/vol2
	gluster volume start vol2
	gluster volume status vol2
	gluster volume info vol2
		type: distribute

## client side
	vim /etc/fstab
		gl3:/vol2 /mnt/vol2 glusterfs default 0 0
	save file
	systemctl daemon-reload
	mount -a
	df -h
	
# delete

## client
	umaount /mnt/vol2
	vim /etc/fstab
		comment line
	
## server
	gluster volume stop vol2
	gluster volume status
	gluster volume info vol2
	gluster colume delete vom2

# set limited
	
## server
	gluster volume create vol1 replica 3 g1:/glustervolume/vol1 g2:/glustervolume/vol1 g3:/glustervolume/vol1
	gluster volume list
	gluster volume info
	gluster volume start vol1

## client
	vim /etc/fstab
		gl3:/vol2 /mnt/vol2 glusterfs default 0 0
	systemctl daemen-reload
	mount -a
	df -h

## server
	gluster volume quota vol1 list
	gluster volume quota vol1 enable
	gluster volume limit-usage / 50MB
	df -hP .
	head -c 5-MB /dev/zero > file1 ===>> make file with 50MB 
	du -sh * ===>> show directory hajm
	mkdr dir1 dir2
	gluster volume quota vol1 limit-usage /dir1 10MB
	gluster volume quota vol1 limit-usage /dir2 10MB
	
# resize

## server
	gluster volume list
	gluster volume info vol1
	gluster volume create vol2 g1:/glustervolume/vol2 g2:/glustervolume/vol2 g3:/glustervolume/vol2
	gluster volume start vol2
	gluster volume status vol2
	gluster volume info vol2
	
## client
	vim /etc/fstab
		gl3:/vol2 /mnt/vol2 glusterfs default 0 0
	systemctl daemon-reload
	mount -a
	df -h
	




	