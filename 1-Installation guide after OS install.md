Guide written to get Hassio installed on Debian 9.6
===

## Check version
```bash
#run command below in Terminal or SSH session
lsb_release -a
```
```
Tested version (details)
// Distributor ID: Debian
// Description:    Debian GNU/Linux 9.6 (stretch)
// Release:        9.6
// Codename:       stretch
```
---

## Ensure your installation is fully up2date
```bash
su -
apt-get update && apt-get upgrade
```

## Ensure your user that you created during the setup (not root), has sudo rights.  
Should prompts for a password.  
```bash
sudo -i 

# How to resolve
su -
sudo adduser <username> sudo
exit
exit
# log back in
```

## Ensure following in installed
```bash
ifconfig

#if missing
sudo apt-get install net-tools
```
```bash
sudo

#if missing
#log in as root"
apt-get install sudo
```
---
## Installation of hassio (on Debian)
```bash
#Go step-by-step and ensure you have no errors
sudo -i

apt-get install -y apparmor-utils apt-transport-https \
   avahi-daemon ca-certificates curl dbus jq network-manager \
   socat software-properties-common

curl -sSL https://get.docker.com | sh

<Archived>curl -sL "https://raw.githubusercontent.com/home-assistant/hassio-build/master/install/hassio_install" \
   | bash -s
<Now>
curl -sL "https://raw.githubusercontent.com/home-assistant/hassio-installer/master/hassio_install.sh" | bash -s
```


## Check if Hassio runs : 
```bash
sudo -i
ifconfig
# find the ip address
# browse to http://<ipaddress>:8123
```
---
# Handy tools to install
## lm-sensors
```bash
apt-get install lm-sensors
# To test and see them 
sensors
# If CPU Temp (core_temp) is missing
modprobe coretemp
```
