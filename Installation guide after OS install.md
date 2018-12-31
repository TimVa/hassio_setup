// Guide written for Debian 9.6

// Check version
    lsb_release -a

// Tested version (details)
// Distributor ID: Debian
// Description:    Debian GNU/Linux 9.6 (stretch)
// Release:        9.6
// Codename:       stretch


//Ensure your installation is fully up2date
   su -
   apt-get update && apt-get upgrade

//Ensure your user that you created next to the root user, has sudo rights.  Should prompts for a password.  If sudo is missing check below and come back here

   sudo -i 
        //su -
        //sudo adduser <username> sudo
        //exit
        //exit
        //"log back in"

//Ensure following in installed, if not check comments on how to correct it.
    ifconfig
        // sudo apt-get install ifconfig
    sudo
        //"log in as root"
        // apt-get install sudo

//Installation of hassio (on Debian)
    sudo -i
    apt-get install -y apparmor-utils apt-transport-https avahi-daemon ca-certificates curl dbus jq network-manager socat software-properties-common
    curl -sSL https://get.docker.com | sh
    curl -sL "https://raw.githubusercontent.com/home-assistant/hassio-build/master/install/hassio_install" | bash -s

// Check if Hassio works : 
    sudo -i
    ifconfig
    // find the ip address
    // browse to http://<ipaddress>:8123

// handy tools to install
  apt-get install lm-sensors
  // To test and see them 
  sensors
  //If CPU Temp (core_temp) is missing
  modprobe coretemp


