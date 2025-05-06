# ansible
    sudo apt install ansible
    pip install ansible

    ansible --version

# ansible server
    mkdir workspace
    /etc/ansible/ansible.cfg ===>> old directory has config file
 	you can make configuration everywhere

## vim servers.ini
### First way
    [all]

    web1	ansible_host=191.168.1.105
            ansible_user=behnam
            ansible_ssh_password=123
            ansible_port=22
            ansible_connection=ssh

    web2	ansible_host=191.168.1.110
            ansible_user=milad
            ansible_ssh_password=321
            ansible_port=2222
            ansible_connection=ssh
        
### second way
    [all]
        server1 ansible_host=192.168.1.105
        server2 ansible_host=192.168.1.110
        server3 ansible_host=192.168.1.115
    
    [web]
        server1
    
    [db]
        server2
    
    [lb]
        server3
    
    [all:vars]
        ansible_user=behnam
        ansible_port=22

## vim servers.yaml
    all:
      children:
        webservers:
          hosts:
            192.168.1.105:
              ansible_port: 22
            192.168.1.110:
              ansible_port: 2222
          vars:
            http_port: 80
            
        dbservers:
          hosts:
            db1.behnam.local:
              db_user: admin
              db_pass: 123
            db2.behnam.local:
              db_user: admin
              db_pass: 321
              db_host: 192.168.1.110
              db_port: 22

## command
    ansible --list-hosts all -i /home/behnam/workspace/servers.ini
            all, db, web     direction directory

# moduls
    ansible -m ping all -i servers.ini
    ansible -m ping db -i servers.ini
	ansible -m ping web -i servers.ini
              modul
    ansible -m command -a "uptime" -i servers.ini all
	ansible -m command -a "uname -a" -i servers.ini all
	ansible -m command -a "sudo reboot" -i servers.ini all
    ansible -m command -a "touch /tmp/backup" -i servers.ini all
	ansible -m command -a "cp /etc/passwd /tmp/passwdbk" -i servers.ini all
                        excute 
  vim file1.txt
		behnam	
	sndiblr sll -m copy -a "src=/home/behnam/file1.txt dest=/home/milad/file1.txt" -i servers.ini
		local place
	sndiblr sll -m copy -a "src=/home/behnam/file1.txt dest=/home/milad/file1.txt" -i servers.ini --become --becomeuser root --become-method sudo ===>> switch user
	sndiblr sll -m copy -a "src=/home/behnam/file1.txt dest=/home/milad/file1.txt" -i servers.ini --become --becomeuser root --become-method sudo --ask-become-pass ===>> ask password root
	ansible all -m apt -a "name=nginx atate=present" --become -i servers.ini
	ansible all -m apt -a "name=nginx=4.1.4 atate=present" --become -i servers.ini
	ansible all -m apt -a "name=nginx atate=absent " --become -i servers.ini
	absent ===>> delete
	present ===>> install
	ansible all -m apt -a "upgrade=yes update_cache=yes" --become -i servers.ini 
	
	modul command why we have modul shell ===>> you can't redirect, append, pipe, ;, &&, ||
	row modul ===>> can command in no have python system like sisco




