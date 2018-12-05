# System Files

## Unity Tweak Tools

```
   sudo apt-get install unity-tweak-tool
```

## Chrome

Download and install signing key

```
   wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```

Setup Chrome Repository

```
   echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" | sudo tee /etc/apt/sources.list.d/google-chrome.list
```

Update and install chrome

```
   sudo apt-get update
   sudo apt-get -y install google-chrome-stable
```
