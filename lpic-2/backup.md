# backup
	backup ===>> os level, application level
	backup ===>> 
		/etc ===>> config file
		/home ===>> file users
		/root
		/usr/local ===>> local program script
	proxmox
	veeam ===>> windows
	amanda
	backuppc
	bacula system ===>> data center
	
## tar
	tar -cfv mydir.tar mydir
	cp mydir.tar /opt
	tar -xvf mydir.tar
	tar -tvf mydir.tar ===>> see all file inside without untar
	tar -xvf mydir.tar "file1" "file2" ===>> select file
	tar -xvf mydir.tar --wildcards '*.conf'
	
	tar -czfv mydir.tar.gz mydir ===>> make gzip file
	tar -xzfv mydir.tar.gz
	
	tar -cjfv mydir.tar.bz mydir ===>> make bzip file
	tar -xjfv mydir.tar.bz

## copy
### rsync
	apt install rsync
	rsync -zvh mydir.tar /tmp
	rsync -azvh mydir /tmp ===>> a == directory move
	rsync -azvh mydir behnam@192.168.1.100:/tmp ===>> 
		copy to another server
	rsync -azvh behnam@192.168.1.100:/tmp/mydir /tmp
	rsync -azvh --max-size='200k' mydir behnam@192.168.1.100:/tmp ===>> 
		server transfer file
	rsync -azvh --bwlimit=100 mydir behnam@192.168.1.100:/tmp ===>>
		bandwith limit 
	rsync -azvh --remove-source-file mydir behnam@192.168.1.100:/tmp ===>>
		delte source file

### scp
	scp mydir.tar behnam@192.168.1.100:/tmp
	scp behnam@192.168.1.100:/tmp/mydir.tar .
	scp -r mydir behnam@192.168.1.100:/tmp ===>> directory
	
## dd
	dd if=/dev/sda of=/dev/sdb
	dd if=/dev/sd2 of=/tmp/sda2.img
	dd if=/dev/zero of=zerofile bs=1M count=10





    