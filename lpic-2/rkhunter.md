# rkhunter
    sudo apt update && sudo apt install rkhunter -y
    rkhunter --version ===>> show your version
    vim /etc/rkhunter.conf ===>> config file
        UPDATE_MIRRORS=1
        MIRRORS_MODE=0
        WEB_CMD=""
    rkhunter --update ===>> for update rkhunter
    rkhunter --check ===>> start check
    rkhunter -c ===>> start to check

## cron job
    vim /etc/default/rkhunter.conf ===>> make this file for automatically up scan and update with cron job
        CRON_DAILY_RUN="true"
        CRON_DB_UPDATE="true"
        APT_AUTOGEN="true"
    rkhunter -C ===>> following command