> This work is dedicated to the public domain under CC0 1.0. See LICENSE for details.

# Personal Debian Setup
This is how I personally set up my Debian for desktop use. This involves additional security measures that don't take a cybersecurity expert to implement safely, as well as the installation of a desktop environment (KDE Plasma 6). This is assuming that Debian has been installed from netinst and no desktop environment was selected. I choose no desktop environment so i can practice setting it up myself.

DISCLAIMER: This guide is not meant for beginners. It is meant as a means of hardening Debian without taking too much of the security into own hands.

# Disclaimer
# Step 1: Updating and upgrading
To make sure my system is up to date and I'm downloading the latest software, run the following:
```
sudo apt update && sudo apt full-upgrade
```
# Step 2: Firewall installation (ufw)
To install a simple firewall that doesn´t take a cybersecurity expert to safely operate, I use ufw (uncomplicated firewall). It's nice to have even though my computer is always behind a NAT.
```
sudo apt install ufw
```
```
sudo ufw enable
```
```
sudo ufw default deny incoming
```
```
sudo ufw default allow outgoing
```
And to check that its running correctly, I run
```
sudo ufw status verbose
```
Here's the Debian Wiki for it: https://wiki.debian.org/Uncomplicated%20Firewall%20%28ufw%29

# Step 3: security-misc
To ensure further security hardening that's already been pre-configured by a cybersecurity team, i use `security-misc`. It is developed by Kicksecure. Kicksecure is a Linux Distro designed for in-depth security. This package adds a lot of extra security on top of what Debian already has, including permission hardening, extra kernel hardening and more. I enjoy this because it is an extra layer of defensive security already curated by people that know what they're doing. Here is the guide that i follow: https://www.kicksecure.com/wiki/Security-misc#Installation_of_security-misc. Writing it onto this guide would just be copying at this point. I recommend following the steps in the link.

# Step 4: Is AppArmor still running?
Run the following and ensure that AppArmor is active and running.

```
sudo aa-status
```
```
sudo systemctl status apparmor.service
```

# Step 5: A stylish desktop environment
This step installs the standard KDE Plasma 6 desktop environment. Here is the wiki for this step: https://wiki.debian.org/KDE

First off install the DE:
```
sudo apt install kde-standard
```

If this didn't install SDDM already, install it and reconfigure it
```
sudo apt install sddm
```
```
sudo dpkg-reconfigure sddm
```

# Step 6: Reboot into your new desktop environment
```
sudo reboot
```
