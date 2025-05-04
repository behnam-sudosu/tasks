# partitioning

        lsblk
        lsblk -f
        partion type ===>> linux, raid, swap, lvm
	        file system ===>> ext4, ext3, ext2 ,xfs
        <!-- you can see your partions -->
        fdisk /dev/sdb
        <!-- this is for MBR partions -->
        m ===>> help
        n ===>> add new partiton
        p ===>> print the partition
        d ===>> delete a partion
        t ===>> change partition type
        w ===>> write table to disk an exit

# fdisk /dev/sdb
        p ===>> see partion
        n ===>> partition type
                        primary
                        extended
                partition number (default)
                first sector (default)
                last sector +2G
        t ===>> partion type
                partition number
                L ===>> show Hex code type
                (83) linux
                (82) linux swap
                (8e) linux lvm
                (fd) linux raid
                <!-- type hex code -->
                w ===>> save and exit

# gdisk /dev/sdb
        ? ===>> help
        d ===>> delete a partion
        c ===>> change a partition's name
        l ===>> list known partition types
        n ===>> add a new partition
        p ===>> print the partition table
        q ===>> quit without saving changes
        t ===>> change a partion's code
        w ===>> write table to disk and exit
        
# make file system
        for file system
        mkfs -t ext4 /dev/sdb1
        or
        mkfs.ext4 /dev/sdb1

# type of file system
        ext4, ext3,ext2, xfs, vfat, ptfs, msdos, fat,btrfs, bfs

# mount
        mkdir /mnt/hard
        mount /dev/sdb1 /mnt/hard
        umount /dev/sdb1

# permanent
        vim /etc/fstab
                /dev/sdb1 /mnt/hard ext4 default 0 0
                or
                <!-- find uuid -->
                ls -l /dev/disk/by-uuid
                /dev/disk/by-uuid/(uuid) /mnt/hard ext4 default 0 0
                
        mount -a







