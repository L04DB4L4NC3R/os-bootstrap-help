## Installing kernels

TODO: In progress

* Rolling kernel

```sh
sudo pacman -S linux linux-headers linux-firmware
```

* LTS kernel

```sh
sudo pacman -S linux-lts linux-lts-headers linux-lts-firmware
```

* Xanmod kernel

```sh
yay -S linux-xanmod linux-xanmod-headers
```

Now run mkinitcpio and remake grub config to see the new kernel option in the grub menu. Or you can remove the old kernel
