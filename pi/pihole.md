## PiHole Setup

* Installation is simple:

```
curl -sSL https://install.pi-hole.net | bash
```

Make sure you have a static IP first

* Admin portal password reset

```
pihole -a -p
```

* Adding domains

```
pihole -w <domain>
```

* For bulk adding URLs with domains: `Group Management > Adlists`. In the Address, copy paste the contents on `blocklist.txt`

* After adding domains, update the lists: `pihole -g`
