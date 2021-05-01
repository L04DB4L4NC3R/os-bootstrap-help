### Xinput
This can be used to enable/disable inputs

eg: To disable keyboard

```
# look for AT Translated Set 2 keyboard
# note its id
# note its slave keyboard id (we shall call it sid)
xinput --list

# to disable keyboard
xinput float <id>

# to enable keyboard again
xinput reattach <id> <sid>
```
