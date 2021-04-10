## Localhost Tunnelling
This will allow you to send traffic to your raspberry pi on your private home network by bypassing ISP NAT entirely

You can do this using *ngrok* but it limits the domain name you can have as well as does not provide static domains in the free tier.

The best way is to setup a wireguard tunnel between the raspberry pi and a server on your VPS, then change iptables to forward ip (v4 or v6) traffic to the VPS to the pi.

* Install wireguard on VPS as well as Raspberry pi

* Wireguard works in public/private key pairs so generate them in both machines:

```
# generates private key with specific permission and add to wireguard conf
(umask 077 && printf "[Interface]\nPrivateKey = " | sudo tee /etc/wireguard/wg0.conf > /dev/null)

# generates public key and display it
wg genkey | sudo tee -a /etc/wireguard/wg0.conf | wg pubkey | sudo tee /etc/wireguard/publickey
```

* Edit the wireguard conf at `/etc/wireguard/wg0.conf` in both machines:

**VPS**

```
[Interface]
PrivateKey = <--- already there if previous step ran correctly
ListenPort = 80 <--- whichever port you want to forward
Address = 192.168.4.1 <--- this will be the private IP for VPS in wireguard tunnel

[Peer]
PublicKey =  ums9y... <--- public key from the machine at home
AllowedIPs = 192.168.4.2/32 <----- private IP & subnet for raspberry pi in wireguard tunnel
```

**Raspberry Pi**

```
[Interface]
PrivateKey = <---- already there if previous step ran correctly
Address = 192.168.4.2

[Peer]
PublicKey = GJtb+O7nnT... <---- public key from VPS
AllowedIPs = 192.168.4.1/32
Endpoint = <IP>:80 <----- public IP of server along with the port to be forwarded
PersistentKeepalive = 25 <---- send a packet every 25 seconds to keep the connection active
```


* Enable wireguard on both machines

```
sudo systemctl start wg-quick@wg0
sudo systemctl enable wg-quick@wg0
```

* Now both machines will be able to ping each other using the private IPs that we have
assigned for them in the wireguard tunnel

`Note`: <IP>/24 means that there are 32-24 = 8 bits worth of addresses available in the subnet. So total number of IPs available = 2^8

* From the current network configuration, see the network interface on the VPS:

```
# in our case the active interface is eth0
sudo ip -4 addr show scope global
```

* Change IP rules for forwarding on the VPS

```
# so that nobody can forward packets
sudo iptables -P FORWARD DROP

# forward traffic on eth0 interface to the wireguard wg0 interface
# only do so for port 80
sudo iptables -A FORWARD -i eth0 -o wg0 -p tcp --syn --dport 80 -m conntrack --ctstate NEW -j ACCEPT
# allow ingress and egress on this route
sudo iptables -A FORWARD -i eth0 -o wg0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i wg0 -o eth0 -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
```

* Change source and destination address of packet while forwarding on the VPS

```
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 192.168.4.2
sudo iptables -t nat -A POSTROUTING -o wg0 -p tcp --dport 80 -d 192.168.4.2 -j SNAT --to-source 192.168.4.1
```

* Make the iptables persist after reboot/failure

```
sudo apt install netfilter-persistent
sudo netfilter-persistent save
sudo systemctl enable netfilter-persistent
```

* Enable IPv4/IPv6 forwarding in VPS, edit `/etc/sysctl.d/wireguard.conf`:

```
net.ipv4.ip_forward=1 # uncomment this line in /etc/sysctl.conf also
net.ipv6.conf.all.forwarding=1
net.ipv6.conf.default.forwarding=1
net.ipv6.conf.eth0.proxy_ndp=1
```

* Done!

* References
	* https://gist.github.com/MartinBrugnara/cb0cd5b53a55861d92ecba77c80ba729
	* https://golb.hplar.ch/2019/01/expose-server-vpn.html
