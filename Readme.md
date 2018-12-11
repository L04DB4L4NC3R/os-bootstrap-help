# Linux 16.04

3rd December 2018
after apocalypse

1. Nvidia And Power
   * Settings and drivers
     * cuda and cudnn
   * Power - tlp and fast get

2. vim
   * vimrc
   * vim plug

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

Paste the export line at the end of ~/.bashrc

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
