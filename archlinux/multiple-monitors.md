### Multiple monitor configurations

See [this](https://wiki.archlinux.org/index.php/Multihead#Separate_screens)

* Xrandr is a utility which helps work with displays. To open an application is a particular display, ie in display 1 screen 0:

```sh
DISPLAY=1:0 alacritty &
```

* Seeing what all monitors are connected:

```sh
xrandr --list-monitors
```

* Screen mirroring at a particular resolution:

```sh
xrandr --output HDMI-1-0 --mode 1920x1080 --pos 0x0
```

* Xinerama is the old way of doing genuine multihead X. Xinerama combines all monitors into a single screen (:0) making it possible to drag windows between screens.

* Download `arandr`, which is a GUI for xrandr
