# NTP server

## server
    apt install ntpdate ===>> befor install ntp
    ntpdate -v pool.ntp.org
    ir.pool.ntp.org

    apt update && apt install ntp
    apt install chrony ===>> same as ntp

    systemctl status ntp.service
    ntpq -p ===>> show information
    vim /etc/ntp.conf
        pool 192.168.1.100 iburst
        pool ir.pool.ntp.org iburst
    systemctl restart ntp

## client
    apt update && apt install ntp
    vim /etc/ntp.conf
        #poll 0.ubuntu.pool.ntp.org iburst
        pool 192.168.1.100 iburst
    systemctl restart ntp
    ntpq -p
