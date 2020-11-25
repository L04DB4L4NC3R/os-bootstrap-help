## Mount external hard disk

* Create a dir in the /mnt folder

```sh
mkdir /mnt/hdd
```

* Figure out the hard disk using `lsblk` and mount it on /mnt/hdd

```sh
sudo mount /dev/sda /mnt/hdd
```

* Update fstab to mount the drive at boot

```sh
# Get block ID of the hard disk
blkid

# Open /etc/fstab and add these lines, where UUID is the blkid of the drive
# Note that in fstype, enter the formatting of the drive, eg: ntfs or ext4
# If it is ntfs then sudo apt install ntfs-3g
# If it is exfat then sudo apt install exfat-fuse
UUID=5C24-1453xxxxxxxxxxxx	/mnt/mydisk	fstype defaults,auto,users,rw,nofail 0 0
```
