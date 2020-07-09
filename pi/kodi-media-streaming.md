## How to start Kodi in Headless mode

```
git clone https://github.com/topfs2/xbmc.git kodi-helix-headless

cd kodi-helix-headless/

git checkout helix_headless

./bootstrap

./configure --prefix=/opt/kodi-helix-headless/

make -j `nproc`

sudo make install -j `nproc`

/opt/kodi-helix-headless/lib/kodi/kodi.bin --headless &
```
