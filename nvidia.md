## Setting up Nvidia

Note that if you use a custom kernel (other than linux and linux-lts), this might not work.

* Install nvidia, nvidia-utils and nvtop

```sh
# nvidia server
sudo pacman -S nvidia

# nvidia utilities
sudo pacman -S nvidia-utils

# monitoring tool
sudo pacman -S nvtop
```

* Download nvidia-dkms. This installs the appropriate nvidia kernel mode setting (kms) for your kernel and is recommended if you are using a custom kernel.

```sh
sudo pacman -S nvidia-dkms
```

* Add the kernel modules in the `/etc/mkinitcpio.conf` in the MODULES array:

```sh
MODULES=(nvidia nvidia_modeset nvidia_uvm nvidia_drm)
```

* Run mkinitcpio

```sh
mkinitcpio -p <your kernel name>
```

* Enable direct rendering (drm) in grub:

```sh
# Edit the /etc/default/grub file and add in the 
# GRUB_CMDLINE_LINUX_DEFAULT
# The loglevel shows the logs while booting
# nouveau is the builtin default nvidia kernel module and it
# sucks, so this also turns that off
# These are the kernel flags and can also be added in the 
# linux section in grub settings during boot (by pressing e)
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 nvidia-drm.modeset=1 nouveau.modeset=0"
```

* Make grub config

```sh
sudo grub-mkconfig -o /boot/grub/grub.cfg

# or 
sudo update-grub
```
