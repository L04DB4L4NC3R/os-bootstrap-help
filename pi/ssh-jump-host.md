## Setting up an SSH jump host
Access your raaspberry pi from anywhere without port forwarding on the router

* SSH into your raspberry pi and edit the `/etc/ssh/sshd_config` file to change this:

```
GatewayPorts yes
```

* Restart sshd

```sh
sudo systemctl restart ssh
```

* Create a jump host on Linode or any hosting provider. Let us call its domain name `bastion`. You can use IP address also

* Create a remote port forward using SSH in the raspberry pi

```sh
# This will forward all traffic on port 8080 of bastion to port 22 of the raspberry pi
ssh -R 8080:localhost:22 root@bastion
```

* Go into the machine that you want to access the rpi from and setup a local port forward using SSH

```sh
# This will forward all traffic of the bastion host port 8080 to the localhost (our machine)
ssh -L 8080:localhost:8080 root@bastion
```

* SSH into your rpi from the machine using the forward port

```sh
ssh -p 8080 pi@localhost
```
