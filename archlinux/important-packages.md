## Some useful packages

```sh
# feh: image viewer
# mpv: video player
# alacritty: terminal emulator
# qutebrowser: browser
# cava: sound visual effects
# tranmission-gtk: torrent client
# youtube-dl: for opening videos in mpv
# mpd: music player
# newsboat: RSS feed reader
# fzf: fuzzy finder
# tty-clock: terminal based clock
# nemo: bful file manager (cinnamom uses it)
# nitrogen: Wallpaper setter
# picom: Compositor
# dmenu: Suckless menu
# htop: Monitor usage
# pandoc: Document converter
# zathura: PDF viewer
# network-manager-applet: nm-applet, NetworkManager applet
# lsd: ls command with icons and colors
# redshift: night mode
# picom: Compositor
# neofetch: Fetch details about the system
# xclip: X11 clipboard manager
# obs-studio: video record and stream
# blueberry: GUI for Bluetooth Configuration
# arandr: GUI for multiple monitors
# pavucontrol: pulseaudio volume control
# dunst: notification system that uses libnotify
sudo pacman -S feh mpv newsboat alacritty \
 qutebrowser transmission-gtk youtube-dl mpd \
 newsboat fzf nemo nitrogen picom dmenu htop \
 zathura zathura-pdf-poppler pandoc texlive-core \
 network-manager-applet lsd redshift picom neofetch \
 xclip blueberry arandr pavucontrol dunst
```

---

## Some important AUR packages

```sh
# subliminal: download subtitles
# spotify: official spotify client
# nerd-fonts-complete: nerd fonts
# chromium-widevine: for decrypting DRM content for qutebrowser so netflix and all play
# deadbeef: music player
yay -S subliminal spotify nerd-fonts-complete \
chromium-widevine deadbeef
```
