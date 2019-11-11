# mal-docs
A simple collection of solutions to various troubles I have faced in the past.
The following notes act merely as notes-to-self. They are, however, made
public, in case some poor soul should encounter a similar problem.

## Installing packages onto offline system
### Context
### Solution

## Connecting to wpa enterprise wi-fi through nmcli 
### Context
### Solution
Configured file `/etc/NetworkManager/system-connections/eduroam`.
``` bash
[connection]
id=eduroam
uuid=<your_uuid>
type=wifi
interface-name=<your_interface>
permissions=

[wifi]
mac-address=<your_mac-address>
mac-address-blacklist=
mode=infrastructure
ssid=eduroam

[wifi-security]
key-mgmt=wpa-eap

[802-1x]
eap=peap;
identity=<your_identity>
password=<your_password>
phase1-peapver=0
phase2-auth=mschapv2

[ipv4]
dns-search=
method=auto

[ipv6]
addr-gen-mode=stable-privacy
dns-search=
method=auto
```

## Changing screen brightness with xbacklight
### Context
### Solution
Solution based on the following [answer](https://askubuntu.com/a/715310).

Configured file `/etc/X11/xorg.conf`
``` bash
Section "Device"
Identifier  "Card0"
Driver      "intel"
Option      "Backlight" "/sys/class/backlight/intel_backlight"
EndSection
```
