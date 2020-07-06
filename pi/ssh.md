## To get SSH to work on raspberry pi

* Run the following command and enable ssh:

```sh
sudo raspi-config
```

* Get your local IP

```sh
hostname -i

# or
ip addr | grep 192.168
```

* You can now SSH!

---

## Setting up SSH keys

* Go to raspberry PI and generate the SSH key pair (id_rsa and id_rsa.pub)

```sh
ssh-keygen -t rsa
```

* Add the key in known_hosts

```sh
cat id_rsa.pub >> ~/.ssh/known_hosts
```

* Do not keep the private key on the rpi for safety concerns. Copy it over. To connect using it:

```sh
ssh -i id_rsa pi@<ip-addr-of-pi>
```
