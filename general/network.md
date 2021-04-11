## Network debugging

* Make sure NetworkManager is running

```sh
sudo systemctl status NetworkManager
```

* If not then download and enable it

```sh
sudo pacman -S NetworkManager
# or
sudo apt install network-manager

sudo systemctl enable --now NetworkManager
```

* Use nmcli or nmtui

```sh
nmtui
```

* In arch check wifi menu

```sh
wifi-menu
```

* If interface issue is there then check ifconfig:

```sh
ifconfig
iwconfig

# for debian based -> wireless interface is wlan0
# for arch its wlps0..
```

* If interface not there then check dmesg (kernel messages)

```sh
# iwlwifi is kernel module for managing wifi
dmesg | grep iwlwifi
```

* If firmware issue:

```sh
# and reboot
sudo pacman -S linux-firmware
```

* If not fixed run lspci to see pci devices. This will show model number of network card. Check for firmware online

```sh
lspci
```
