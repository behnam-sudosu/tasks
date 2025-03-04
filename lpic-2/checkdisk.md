# ckeck disk
    notice you have umount disk befor check
    umount /dev/sdb1
    fsck /dev/sdb1
    fsck -f /dev/sdb1 ===>> check force
    fsck -f -y /dev/sdb1 ===>> -y = yes
    fsck -n /dev/sdb1 ===>> -n = dry on ask everything

# recovery from superblock
    mkfs.ext4 /dev/sdb1
        save your superblock number
    fsck -b 294912 /dev/sdb1
    fsck -b 294912 -y /dev/sdb1
    fsck -b 294912 -f -y /dev/sdb1
    
# tune2fs
    tune2fs -l /dev/sdb1 ===>> give you more information
    tune2fs -L (DATA) /dev/sdb1 ===>> set lable for disk
    tune2fs -i 7 /dev/sdb1 ===>> after seven days check disk
    tune2fs -c 3 /dev/sdb1 ===>> after mount and umount check disk

# dumpe2fs
    dumpe2fs /dev/sdb1 ===>> more information from tune2fs
        superblock back up
    dumpe2fs /dev/sdb1 | grep -i superblock

# debugfs
    debugfs /dec/sdb1 ===>> go inside disk
        ls
        lsdel ===>> show delete file
        q ===>> quit

# xfs
    mkfs.xfs /dev/sdb1
    xfs_info /dev/sdb1 ===>> more information
    xfs_repair /dev/sdb1
    apt install xfsdump
    xfsdump -f /mnt/mybackup/backup3 /mnt/data ===>> backup
        lable ===>> test
        lable ===>> test
    xfsrestore -f /mnt/mybackup/backup3 /mnt/data ===>> restore backup
    xfsrestore -I ===>> more information about where restored

# S.M.A.R.T
    sudo apt install smartmontools
    smartctl -i /dev/sdb ===>> monitoring disk
    smartctl -H /dev/sdb ===>> health check
    smartctl -t short and long /dev/sdb ===>> test disk read and write
    smartctl -a /dev/sdb ===>> test disk read and write
    vim /etc/default/smartmontools
        enable_smart="/dev/sdb /dev/sdc" ===>> check these disk
        smartd_opts="--interval=1800" ===>> check after this time
        start_smartd=yes ===>> all time bring up my smartd
    save the file
    service smartd restart






