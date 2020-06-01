## Setting the gtk theme

```sh
sudo pacman -S arc-gtk theme
gsettings set org.gnome.desktop.interface gtk-theme "arc-gtk-theme"
```

## Preferring dark theme

```sh
# Add the following line in this file:
# gtk-application-prefer-dark-theme = true
sudo vim /usr/share/gtk-3.0/settings.ini
```
