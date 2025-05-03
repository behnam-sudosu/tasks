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
    ansible -m ping all -i /home/behnam/workspace/servers.ini
    ansible -m ping db -i /home/behnam/workspace/servers.ini
	ansible -m ping web -i /home/behnam/workspace/servers.ini
              modul





