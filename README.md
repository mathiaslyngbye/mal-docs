# mal-docs
A simple collection of solutions to various troubles I have faced in the past.
The following notes act merely as notes-to-self. They are, however, made
public, in case some poor soul should encounter a similar problem.

# Installing packages onto offline system
## Context
## Solution

# Connecting to wpa enterprise wi-fi through nmcli 
## Context
## Solution

# Changing screen brightness with xbacklight
## Context
## Solution
Solution based on the following [answer](https://askubuntu.com/a/715310).

Configured file `/etc/X11/xorg.conf`
`` bash
Section "Device"
Identifier  "Card0"
Driver      "intel"
Option      "Backlight" "/sys/class/backlight/intel_backlight"
EndSection
``
