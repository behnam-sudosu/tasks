# samba or smb
	share folder

## install
	sudo apt update && sudo apt install samba
	
## config file    
    make disk
	mount it
	mkdir -p /srv/samba/anonymous_shares
	chmod 0777 //srv/samba/anonymous_shares
	chown nobody:nogroup /srv/samba/anonymous_shares
	cd /etc/samba
		smb.conf
		vim smb.conf
			workgroup = WORKGROUP
			[printers]
			[Anonymous]
				comment = Anonymous File server share
				path = /srv/samba/anonymous_shares
				browseable = yes
				read onlu = no
				writeable = yes
				guest ok = yes
			save file
			
## command test          
    testparm ===>> test for everythin is ok
    service smbd restart
    smbcontrol smbd reload-config ===>> this command help you your user dosn't conction refuse
    sudo apt install smbclient cifs-utils
    smbclient -L localhost
    smbstatus ===>> who is use this
    net status shares ===>> show information


# easy
	server
		sudo apt update
		sudo apt install samba
		vim /etc/samba/smb.conf
			[share]
			path = /home/USERNAME/share
			browseable = yes
			read only = no
			guest ok = yes
		save file
		sudo systemctl restart smbd
		sudo ufw allow samba

	client
		sudo apt update
		sudo apt install cifs-utils smbclient
		smbclient //IP_ADDRESS/share -N
		sudo mount -t cifs //IP_ADDRESS/share /mnt -o guest
	permanent
		sudo vim /etc/fstab
			//IP_ADDRESS/share /mnt/share  cifs  guest,uid=100  0  0





			