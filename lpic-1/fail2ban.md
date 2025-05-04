# fail2ban
    sudo apt update && sudo apt install fail2ban
    
    cd /etc/fail2ban
        /filter.d ===>> config file all application
    systemctl status fail2ban.service ===>> it's not active
    
    touch jail.local

    vim jail.local
        [sshd]
        enabled = true
        banaction = iptables-multiport
        maxretry = 10
        findtime = 43200
        bantime = 86400
    sytemcttl restart fail2ban.service


    