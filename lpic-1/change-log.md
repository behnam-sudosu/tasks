# change log directory
    sudo vim /etc/rsyslog.d/50-default.conf
    cron.* ===>> /var/log/cron.log

# make file
    sudo touch /var/log/cron.log
    sudo chmod 640 /var/log/cron.log
    sudo chown syslog:adm /var/log/cron.log

    sudo systemctl restart rsyslog