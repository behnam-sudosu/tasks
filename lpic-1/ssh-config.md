# ssh config

## directory
    cd /etc/ssh
        ssh_config ===>> client side
            port 22
        sshd_config ===>> server side
            port 22
            AddressFamily any ===>> ipv4 and ipv6
            ListenAddress 192.168.1.100
            ListenAddress : :  ===>> ipv6
            PermitRootLOgin no ===>> root can login
            PubkeyAuthentication yess ===>> only use public key
            PasswordAuthentication no ===>> no login with password
            MaxAuthTries 3
            MaxSessions 5
            PermitEmptyPasswords no
    systemctl restart sshd
    cd /etc/ssh/sshd.config.d ===>> if there is file here change it 

## config file
    cd ~/.ssh
        mkdirconfig.d
        touch config
        vim config
            include /home/behnam/.ssh/config.d/*
            Host srv1
                HostName 192.168.1.100
                User behnam
                Port 22
## command
    ssh-keygen
    ssh-copy-id behnam@192.168.1.100


