## Repairing bootloader in linux

In a live boot environment:

```sh
# mount main user partition
sudo mount /dev/sda2 /mnt

# mount boot partition
sudo mount /dev/sda1 /mnt/boot/efi

# mount all necessary linux filesystem dirs
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo cp -n /etc/resolv.conf /mnt/etc/

# change root to the mounted filesystem
sudo chroot /mnt
# reinstall grub and linux
apt install --reinstall grub-efi-amd64 linux-generic linux-headers-generic
# update initramfs
update-initramfs -c -k all
# update grub
sudo update-grub
```
