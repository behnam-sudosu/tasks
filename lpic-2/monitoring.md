# monitoring ram & cpu & disk
    vmstat
    free
        -m ===>> megabite
        -h ===>> human readable
        -g ===>> gigabite
    top
        1 ===>> show all core cpu
        d ===>> delay
        k ===>> kill process id
        r ===>> renice process
    stress-ng -c 1
    htop
    uptime
    htop
    sar 1 10

# network
    ifconfig
    netstat -s or -ie
    iftop
    nload
    iperf -s
    iperf -c (ip server)
    iptraf-ng -i ens37

# graph
    cacti
    zabbix
    grafana
    netdata
    collectd
    collectd web





