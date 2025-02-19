# master&slave

    db1 ip address ===>> 192.168.1.100
    db2 ip address ===>> 192.168.1.101

    master ===>> db1
    slave ===>>db2

## master
    vim /etc/hosts
        192.168.1.100 db1
        192.168.1.101 db2

    ping db2
    apt update && apt install mariadb-server
    ss -ntlp ===>> show your port and ip
        3306 ===>> database port
        default ===>> 127.0.0.1:3306
    vim /etc/mysql/mariadb.conf.d/50-server.cfg
        bind-address       = 27.0.0.1 ===>> line 27 change it to your ip address
        bind-address       = 192.168.1.100
        ## at the end of file add this
        server-id          = 1
        log_bin            = /var/log/mysql/mysql-bin.log
        max_binlog_size    = 100M
        relay_log          = /var/log/mysql/mysql-relay-bin
        relay_log_index    = /var/log/mysql/mysql-relay-bin.index
    save the file
    systemctl restart mariadb.service
    systemctl status mariadb.service ===>> active and run
    ss -ntlp
        default ===>> 192.168.1.100:3306

        

## slave
    vim /etc/hosts
        192.168.1.100 db1
        192.168.1.101 db2
    
    ping db1
    apt update && apt install mariadb-server
    ss -ntlp ===>> show your port and ip
        3306 ===>> database port
        default ===>> 127.0.0.1:3306
    vim /etc/mysql/mariadb.conf.d/50-server.cfg
        bind-address       = 27.0.0.1 ===>> line 27 change it to your ip address
        bind-address       = 192.168.1.101
        ## at the end of file add this
        server-id          = 2
        log_bin            = /var/log/mysql/mysql-bin.log
        max_binlog_size    = 100M
        relay_log          = /var/log/mysql/mysql-relay-bin
        relay_log_index    = /var/log/mysql/mysql-relay-bin.index
    save the file
    systemctl restart mariadb.service
    systemctl status mariadb.service ===>> active and run

## mysql
### master
    mysql -u root -p
    ### make use
        CREATE USER 'replication'@'%' identified by '12345678';
        % ===>> all databases
    ### permision
        GRANT REPLICATIONSLAVE ON *.* TO 'replication'@'%';
    ### privilege
        FLUSH PRIVILEGES;
    SHOW MASTER STATUS; ===>> give you file(mysql-bin.000001) and position(780)

### slave
    mysql -u root -p
        STOP SLAVE; ===>> you must stop your slave
        CHANGE MASTER TO MASTER_HOST = 'db1', MASTER_USER = 'replication', MASTER_PASSWORD = '12345678', MASTER_LOG_FILE = 'mysql-bin.000001', MASTER_LOG_POS = 780;
        START SLAVE;
        SHOW SLAVE STATUS \G


# DONE




