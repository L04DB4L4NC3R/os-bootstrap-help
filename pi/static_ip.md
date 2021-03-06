## How to configure static IP for the raspi

Note that this requires you to configure your DHCP daemon. For the pre-requisites:

* Your network interface:

```sh
# select the network interface to configure static IP for
ifconfig
```

* Default Gateway IP (IP of your router)

```sh
route -n
```

* DNS server IP. Some good ones are listed below:
	* Cloudflare: `1.1.1.1` and `1.0.0.1`
	* Google: `8.8.8.8`
To check which one you have at the moment, you can check your DNS resolution file:

```sh
cat /etc/resolv.conf
```

* To find your raspberry pi in the local network:

```
# scan local IP range and subnet to find potential IP of raspberry pi
# once you find it, ssh into it
 nmap -sP 192.168.0.0/24
 ```

* Now Comes to the editing part:

```sh
# open dhcp config for editing
sudo vim /etc/dhcpcd.conf

# Add the following lines at the top:

interface wlan0 # or eth0 or whatever interface u use

static ip_address=192.168.1.99 # this will always be your IP when you connect to this gateway

static routers=192.168.1.1 # default gateway IP

static domain_name_servers=202.62.64.3 8.8.8.8 # space separated list of DNS servers
```

* Save and reboot!

* NOTE: In some cases your dhcpcd conf file will automatically reset at boot. This might be because of the `systemd-resolved` daemon running in the background. Disable it if that's the case

```sh
sudo systemctl disable --now systemd-resolved
```
