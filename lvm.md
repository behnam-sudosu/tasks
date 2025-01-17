# Lvm

## Partion
        lsblk
        lsblk -f
        fdisk /dev/sdb1
        fdisk /dev/sdc1
        n ===>> partition type
                        primary
                        extended
                partition number (default)
                first sector (default)
                last sector (all)
        t ===>> change partion type
        l ===>> list known partition table
        (8e) linux lvm
        w ===>> save and exit

## Physical Volumes(PV)
        sudo apt install lvm2
        pvdisplay
        or
        pvs
        <!-- create  -->
        pvcreate /dev/sdb1 /dev/sdc1
        <!-- remove -->
        pvremove /dev/sdb1
        <!-- scan -->
        pvscan

## Volume Groups(VG)
        vgdisplay
        or
        vgd
        <!-- create -->
        vgcreate (myvg) /dev/sdb1 /dev/sdc1
        <!-- reduce -->
        vgreduce (myvg) /dev/sdc1
        <!-- extend -->
        vgextend (myvg) /dev/sdc1
        <!-- rename -->
        vgrename (myvg) (vg-ssd)

## Logical Volume(LV)
        lvdiaplay
        or
        lvs
        <!-- create -->
        lvcreate --name lvdisk1 --size 12G vg-ssd
        or
        lvcreate -l 100%FREE -n vg-ssd
        <!-- remove -->
        lvremove /dev/vg-ssd/lvdisk1
        <!-- rename -->
        lvrename /dev/vg-ssd/lvdisk1 lvdisk2
        <!-- extend -->
        lvextend -L10G /dev/vg-ssd/lvdisk2
        <!-- if you want to extend you must add final volum -->
        <!-- reduce -->
        lvreduce -L2G /dev/vg-ssd/lvdisk2
        <!-- THIS MAY DESTROY YOUR DATA -->

## file system
        mkfs.ext4 /dev/vg-ssd/lvdisk2
        mount /dev/vg-ssd/lvfisk2 /mnt
        ls -l /dev/mapper
        ls -l /dev/sidk/by-uuid

## permanent
        vim /etc/fstab
                /etc/disk/by-uuid/(UUID) /mnt ext4 defaults 0 0
        mount -a





