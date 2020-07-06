## How to configure static IP for the raspi

Note that this requires you to configure your DHCP daemon. For the pre-requisites:

* Your network interfacex:

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
