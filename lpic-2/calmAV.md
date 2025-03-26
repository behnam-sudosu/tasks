# ClamAV

## install
    sudo apt update && sudo apt install clamav
    clamscan --version ===>> show version
   
### update   
    sudo systemctl stop clamav
    freshclam ===>>> update database
    sudo systemctl stop clamav
    
### command    
    clamscan /path/to/file ===>> scan a file
    clamscan -r /path/to/direcroty ===>> scan a directory
    clamscan -r --bell -i / ===>> check all system
        -r ===>> recursive
        --bell ===>> if find viruse make a noise
        -i ===>> show file infected
    clamscan -r --remoce /path/to/directory ===>> scan and remove infected
    clamscan -r --move=/home/user/quarantine /home/user ===>> quarantine
    /var/log/clamav/clamav.log ===>> log file

## cronjob
    crontab -e
        014 * * * clamscan -r /home --remove --log=/var/log/clamav_scan.log