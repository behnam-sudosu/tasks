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
    fsck -b /dev/sdb1
    fsck -b -y /dev/sdb1
    fsck -b -f -y /dev/sdb1


