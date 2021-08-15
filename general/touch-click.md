touch /etc/X11/xorg.conf.d/99-synaptics-overrides.conf

Add the following lines and reboot:
```
Section  "InputClass"
    Identifier  "touchpad overrides"
    Driver "libinput"
    MatchIsTouchpad "on"
    Option "Tapping" "on"
    Option "TappingButtonMap" "lmr"
EndSection
```
