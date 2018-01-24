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

## Fetch the source files

It's advised to use the releases rather than current git code.  
Current github code may contain untested features and code. 

Head over to the official Bismuth Github repo, releases: https://github.com/hclivess/Bismuth/releases  
Unless you need a specific version, pick the latest one. As for now, this is 4.2.2.7.  
Copy the link of the "Source Code (tar.gz)" file. Mine is https://github.com/hclivess/Bismuth/archive/4.2.2.7.tar.gz

Back to your Ubuntu box, fetch the file where you want it installed, like your home dir, and extract it:
```
cd
wget https://github.com/hclivess/Bismuth/archive/4.2.2.7.tar.gz
tar -zxvf 4.2.2.7.tar.gz
```
It extracts itself under Bismuth-4.2.2.7

## Node only

For a node only install, install the needed python modules:

```
pip3 install simple-crypt --no-deps
pip3 install PySocks pycryptodome
```

You may want to edit your config, or just run the node with defaults, and let it sync. Here, I first run a screen, then run the node inside the screen  
```
screen -s NODE
Python3 node.py
```
Then no matter what happens to the ssh connection, I can find my running node when I need to with a `screen -x NODE`.  
> `ctrl-a d` is used to (d)etach from a running screen.

Let your node sync. It will download the bootstrap ledger from the website, then go crazy fetching backlog of blocks. That's ok, give him some time.

## Node and wallet

The wallet does connect to a node.  
So, in order to run your wallet you also need a running node.

Here are the python modules for the node again, from previous paragraph
```
pip3 install simple-crypt --no-deps
pip3 install PySocks pycryptodome
```

And here are the extra modules currently needed for the wallet:
```
sudo apt install python3-tk
pip3 install pillow pyqrcode
```

> I'm aware of `requirementS.txt`, but as it's not always up to date, I prefer to list the individual commands instead.  I will edit once the files on github will be fully updated.

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
Should say "Network time on: yes"  
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
