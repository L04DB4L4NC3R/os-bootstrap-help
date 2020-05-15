## The ultimate startup config for debian based systems
How  Ḻ̷̃0̸͔̈́͠4̶̡̢̈́̚D̴̲̄͊B̸͕̺͆͗4̴͖̠͐L̶̲͑4̴̡͖͗N̶̦͒C̴̣̄3̸̥̒̆Ŕ̷̫͝   does his configs

## Making a bootable USB drive
* Figuring out which is the USB (will be in the /dev or /media)

```bash
lsblk | grep <usb name>
```
For this example lets assume /dev/sdc1

* dd command for conversion

```bash
# sudo dd bs=4M if=<path-to-iso> of=/dev/sd<letter> conv=fdatasync
sudo dd if=<path-to-iso> of=<path-to-dev, eg: /dev/sdc> status="progress"
```

* Voila

3rd December 2018
after apocalypse

1. Nvidia And Power
   * Settings and drivers
     * cuda and cudnn
   * Power - tlp and fast get

2. vim
   * vimrc
   * vim plug
   * Building vim from source (for ycm)
```bash
https://github.com/ycm-core/YouCompleteMe/wiki/Building-Vim-from-source
```

3. audio
   * pulseeffects

4. Misc
   * system
     * chrome
     * unity tweak tool


### Touchpad

<br />

```bash
DO NOT RUN THIS  sudo apt-get install xserver-xorg-input-synaptics sudo reboot
```

<br />

### nodejs download

```
curl -sL https://deb.nodesource.com/setup_10.x | sudo bash -
sudo apt-get install -y nodejs`
```

<br />


### golang download

Paste the export line at the end of ~/.profile

```
sudo tar -C /usr/local -xzf go1.11.2.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
```

<br />

### SSH keygen

``` 
ssh-keygen -t rsa
cat ~/.ssh/id_rsa.pub
```

### Docker download

```
sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common


curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88



sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

sudo apt-get update

sudo apt-get install docker-ce

sudo groupadd docker

sudo usermod -aG docker $USER
```

<br />

### docker-compose

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
```

<br />

### heroku cli

```
sudo snap install --classic heroku
```

<br />

### Enable exFAT on ubuntu

```
sudo add-apt-repository universe
sudo apt update
sudo apt install exfat-fuse exfat-utils
```


### Additional tips
* How to install from a list of .deb packages
```bash
sudo dpkg -i *.deb
```
