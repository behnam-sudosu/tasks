# raid
	raid ===>> redundant array of independent disks
	we need sdb and sdc
	lsblk -o +fstype ===>> show disk with file system
	partion type ===>> linux, raid, swap, lvm
	file system ===>> ext4, ext3, ext2 ,xfs
	
-----------------------------------------------------------------------	
		    		raid0		  raid1	      	raid5	      raid6       raid10
min disk	          2	            2	          3	            4	        4

fault tolerance	      0	            1	          1	            2	        2

disk space	          0	           50%	        1disk         2disk	       50%

read speed	         fast	       fast	         slow          slow	       fast

write speed	         fast	       fast	         slow          slow	       fast

cost		         cheap	       high	         high        very high     high

usage               archive    os-pentest-db    web&db        notgood     database
----------------------------------------------------------------------

## we have to way to make raid software raid and hardwere raid	
# disk partion	
	cat /proc/mdstat
	fdisk /dev/sdb
		n ===>> new partion
		t ===>> partion type
		L ===>> show all partion type
		fd ===>> linux raid auto
		w ===>> write and exit
	fdisk /dev/sdc
		n ===>> new partion
		t ===>> partion type
		L ===>> show all partion type
		fd ===>> linux raid auto
		w ===>> write and exit

# partion raid		
	apt install mdadm ===>> if you don't have install it
	mdadm --create --vorbos /dev/md0 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1
	ls /dev/md*
	lsblk
	cat /proc/mdstat
		md0 : active raid0 sdb1 sdc1
	fdisk /dev/md0
		n ===>> new partion
	mkfs.ext4 /dev/md0
	mount /dev/md0 /mnt
		
		




