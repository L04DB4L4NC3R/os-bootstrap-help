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
sudo apt-get install xserver-xorg-input-synaptics sudo reboot

<br />

### nodejs download

```
curl -sL https://deb.nodesource.com/setup_10.x | sudo bash -
sudo apt install nodejs
```

<br />


### golang download

Paste the export line at the end of ~/.bashrc

```
tar -C /usr/local -xzf go1.11.2.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
```

<br />

### SSH keygen

``` 
ssh-keygen -t rsa
cat ~/.ssh/id_rsa.pub
```
