## How to create a VPN server using RPI

* Install openvpn and wget

* Get the openvpn installation script (only runs on Ubuntu, Fedora, CentOS. chmod and execute it as a superuser 

```sh
wget https://raw.githubusercontent.com/Angristan/openvpn-install/master/openvpn-install.sh

chmod +x openvpn-install.sh

sudo ./openvpn-install.sh
```

* This will create a `.ovpn` file. Copy it to the client.

* In the client machine use this to connect to the VPN:

```sh
openvpn <name-of-conf>.ovpn

# or copy it here
sudo cp Downloads/*.ovpn /etc/openvpn/client/client.conf

openvpn /etc/openvpn/client/client.conf
```

* A simple GUI for connecting to VPN can be found in the arch repos:

```sh
sudo pacman -S networkmanager-openvpn
```
