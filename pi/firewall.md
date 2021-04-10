## Setting up a network firewall in raspberry pi
To control incoming/outgoing traffic on the raspberry pi itself

* Install ufw

```
sudo apt install ufw
```

* Set default rule to allow all outgoing but deny all incoming

```
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

* Allow ssh

```
sudo ufw allow ssh # or 22
```

* Allow the ports you want

```
sudo ufw allow 80
```

* Allow port ranges

```
sudo ufw allow 6000:6007/tcp
sudo ufw allow 6000:6007/udp
```

* Allow from specific IPS

```
sudo ufw allow from 203.0.113.4

# only allowed to connect to port 22
sudo ufw allow from 203.0.113.4 to any port 22

# subnets
sudo ufw allow from 203.0.113.0/24
```

* Allow to a specific interface

```
sudo ufw allow in on eth0 to any port 80
```

* Check status

```
sudo ufw status verbose
```

* Enable ufw

```
sudo ufw enable
```

* Disable or reset ufw

```
sudo ufw disable
sudo ufw reset
```
