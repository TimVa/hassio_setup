# Set fix ip address on the server

All commands are executed on the server via SSH session and as root (sudo -i), unless marked differently.  

---
## Disable the GUI network-manager
```bash
systemctl stop NetworkManager.service
systemctl disable NetworkManager.service
```
---
## Find interface
```bash
ls /etc/class/net/
```
The interface name starts with `enp` something.
```Mine is enp0s25```

---
## Configure the interface
Edit file /etc/network/interfaces (with nano) 
```bash
nano /etc/network/interfaces
```
Append following to the file (replace <interface_name> with the name you found in previous section) - Of course adapt with your IP needs.  
```
auto <interface_name>
    iface <interface_name> inet static
        address 192.168.1.250
        netmask 255.255.255.0
        gateway 192.168.1.254
```

---
## Disable DHCP
**NOT NEEDED**
```bash
sudo systemctl stop dhcpcd.service
sudo systemctl disable dhcpcd.service
```
---
## Set DNS servers
Edit file  /etc/resolv.conf (with nano) 
```bash
nano  /etc/resolv.conf
```
Fill in your own DNS server you desire to use.  
Some examples :
* Google --> 8.8.8.8 and 8.8.4.4
* CloudFlare --> 1.1.1.1 and 1.0.0.1
* Local router
* Local ISP DNS servers
```
nameserver 12.34.56.78
nameserver 12.34.56.79
```

---
## Finish
**Cross your fingers and reboot**
No, serious, be sure not to have made some typo's and execute
```bash
reboot
```
