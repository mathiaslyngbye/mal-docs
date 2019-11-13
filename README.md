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
Solution was obtained by pseudo copying the interface file of an 
automatically configured working connection of another computer.

Configure file `/etc/NetworkManager/system-connections/eduroam`, replacing
`<variable>` with your own information (notes below).

``` bash
[connection]
id=<your_ssid>
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


In my case, I created the base file through nmcli with the following command. 

``` bash
nmcli con add type wifi ifname <your_interface> con-name <your_connection_name> ssid <your_ssid>
```

Here both `<your_connection_name>` and `<your_ssid>` are `eduroam`, and
`<your_interface>` is my wifi interface, `wlp2s0` (this interface may be 
obtained through
`ifconfig`). 

Additionally, `<your_mac-address>` may be obtained through `ifconfig`. This is
defined under your wifi interface, prefixed by `ether`. Finally, `<your_identity>` and `<your_password>` are my log-in credentials. In
this case my university mail and password.

## Changing screen brightness with xbacklight
### Context
### Solution
Solution based on the following [answer](https://askubuntu.com/a/715310).

Configure file `/etc/X11/xorg.conf`
``` bash
Section "Device"
Identifier  "Card0"
Driver      "intel"
Option      "Backlight" "/sys/class/backlight/intel_backlight"
EndSection
```

## Enable touchpad tap-to-click
### Context
### Solution
Solution based on the following [answer](https://askubuntu.com/a/1088009).

Configure file `/etc/X11/xorg.conf.d/30-touch.conf` 
(create directories if necessary).
``` bash
Section "InputClass"   
    Identifier "touchpad"  
    Driver "libinput"  
    MatchIsTouchpad "on"  
    Option "Tapping" "on"  
EndSection
```
