# quata
    apt install quota
    quotaoff -a 
    vim /etc/fstab
        defaults
        usrquota
        grpquota
    umount /de/sdb1
    mount /dev/sdb1
    ~/quata
    quotacheck -cug /dev/sdb1
        -c ===>> create
        -u ===>> user
        -g ===>> group
    edquota -U behnam
        blocks   soft   hard   inodes   soft   hard
         kb      70m    100m    
    quotaon -a
    quota /dev/sdb1
    edquota -t ===>> change day expire
    repquota -a ===>> report
    repquota /dev/sdb1