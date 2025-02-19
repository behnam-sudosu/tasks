# collectd
    apt update
    apt install collectd
    systemctl status collectd

# config file
    cd /etc/collectd
    vim collectd.conf ===>> importang part is loadplugin section
    systemctl rstart collectd

# collect data
    cd /var/lib/collectd
    apt install tree
    tree rrd
    apt install git
    git clone https://github.com/httpdss/collectd-web.git
    cd collectd-web
    apt install python
    vim runserver.py
        127.0.0.1 ===>> 0.0.0.0
    save file
    ip -br a
        192.168.1.100
    python runserver.py
    open browser
        192.168.1.100:8888
        
# dependency
    apt install librrds-perl libjson-perl libhtml-parser-perl libcgi-pm-perl







