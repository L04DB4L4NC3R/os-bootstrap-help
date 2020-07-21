## To setup VNC server for the rpi

VNC over SSH tunnel. On the client machine run:

```sh
ssh -L 5901:localhost:5901 -N -f <distant_user>@<server_ip>
```

Make sure the pi is running a vncserver on localhost only:

```sh
# run this first
vncserver :1 -geometry 1280x800 -depth 16 -localhost -nolisten tcp
```

Connect to the vnc using client machine

```sh
xtightvncviewer localhost:1 -compresslevel 9 -quality 4 -depth 8
```
