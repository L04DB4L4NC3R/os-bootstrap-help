## Debugging Systemd

Certain daemons like bluetooth, wifi, wpa_suuplicant etc might not be working on first installation. To debug them:

```sh
# see running systemd daemons
sudo systemctl status

# see info about a particular daemon
sudo systemctl status NetworkManager

# start daemon
sudo systemctl start <service>

# enable daemon to start at boot
sudo systemctl enable <service>

# both previous steps in one line
sudo systemctl enable --now <service>

# see systemd logs
sudo journalctl -xe
```

Whenever you start/stop a service, symlinks are created to the systemd dir `/etc/systemd/system`.
