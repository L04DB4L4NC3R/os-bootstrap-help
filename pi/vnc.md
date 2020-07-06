## To setup VNC server for the rpi

* Allow VNC:

```sh
sudo raspi-config
```

* Install X remote desktop protocol

```sh
sudo apt install xrdp
```

* Get the IP address

```sh
hostname -i

# or
ip addr | grep 192.168
```

* Connect using VNC software on any system by just adding the IP address
