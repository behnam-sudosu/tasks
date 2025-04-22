# rsyslog

## server
    sudo apt update && sudo apt install rsyslog
    rsyslogd -v ===>> show more information
    systemctl status rsyslog
    sudo systemctl start rsyslog
    sudo vim /etc/syslog.conf
        # provides UDP syslog reception
            #module(load="imudp")
            #input(type="imudp" port="514")

            # provides TCP syslog reception
            #module(load="imtcp")
            #input(type="imtcp" port="514")
            uncomment TCP and UDP
    sudo ufw allow 514/tcp
    sudo systemctl restart rsyslog.service

## client
    sudo apt update && sudo apt install rsyslog
    rsyslogd -v ===>> show more information
    systemctl status rsyslog
    sudo systemctl start rsyslog
    sudo vim /etc/syslog.d/50-default.conf
        *.* @@0.0.0.0:514
        *.* @@192.168.122.235
        cron.* @@192.168.122.237:514
    sudo systemctl restart rsyslog.service

## test
    logger 'test from client'
    sudo tail /var/log/syslog