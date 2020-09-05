## How to mount android phones

* Mounting and exchanging media uses the MTP protocol (Media Transfer Protocol)

* Using FUSE (File system over user space), we can create an MTPFS mount on any directory within our filesystem

* Your phone needs to be connected via USB and in file sharing mode, and unlocked.

* Install the following package

```sh
# this contains FUSE 2 as dependency so no need to install it
yay -S simple-mtpfs
```

* List connected android devices

```sh
# lists device and its ID
simple-mtpfs -l
```

* Mount device on a folder called `cell`.

```sh
# 1 is the device ID outputted by the previous command
simple-mtpfs --device 1 ~/cell
```

* Device can now be unmounted from any file explorer or by running the following command

```sh
fusermount -u ~/cell
```
