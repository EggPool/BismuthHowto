# How to install Bismuth Node or wallet on Linux?

This guide is made for Ubuntu. Little should change for other distros.  
The box I used was an Ubuntu 16.04


*WIP*

## Pre-requisites

Python3.5 or later is needed, as well as matching pip
 
> In order to check your python version , use `python3 --version`

Update your system first:  
```
apt update
apt upgrade
```

Install pip if needed:  
```
sudo apt install python3-pip
```

> If pip complains about a new version, you can update it: `pip3 install --upgrade pip`

Other goodies may be of use : 
```
sudo apt install screen htop wget sqlite3
```

## Fetch the source files

It's advised to use the releases rather than current git code.  
Current github code may contain untested features and code. 

## Node only

For a node only install, install the needed python modules:

```
```

## Node and wallet

The wallet does connect to a node.  
So, in order to run your wallet you also need a running node.


## OS config

On the node box, be sure to have enough files limits (replace root by the user the node will run under)
...
nano /etc/security/limits.conf
root soft nofile 65535
root hard nofile 65535
...

```
nano /etc/sysctl.conf
```
Append:  
```fs.file-max = 100000```

```
sysctl -p
```

make sure your time is network synced
```
timedatectl
```
> if network sync is not active, `timedatectl set-ntp on`

Low latency won't do harm
```
echo 1 > /proc/sys/net/ipv4/tcp_low_latency
```

> If your install complains about locales only:
```
export LC_ALL="en_US.UTF-8"
export LC_CTYPE="en_US.UTF-8"
sudo dpkg-reconfigure locales
```

## Node and wallet on distinct hosts

TODO

## Config file

TODO - dedicated page
