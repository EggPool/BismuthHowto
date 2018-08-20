# How to install Bismuth Node or wallet on Linux?

This guide is made for Ubuntu. Little should change for other distros.  
The box I used was an Ubuntu 16.04


## Pre-requisites

Python3.6 or later is needed, as well as matching pip.  

If you need to install a version above what your system ships with, it's recommended to use pyenv.  
https://askubuntu.com/questions/865554/how-do-i-install-python-3-6-using-apt-get#865569  
Pyenv allows you to install many versions of python on a single machine without messgin with the default one, used by the system.
 
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
Unless you need a specific version, pick the latest one. As for now, this is 4.2.6.  
Copy the link of the "Source Code (tar.gz)" file. Mine is https://github.com/hclivess/Bismuth/archive/4.2.6.tar.gz

Back to your Ubuntu box, fetch the file where you want it installed, like your home dir, and extract it:
```
cd
wget https://github.com/hclivess/Bismuth/archive/4.2.6.tar.gz
tar -zxvf 4.2.6.tar.gz
```
It extracts itself under Bismuth-4.2.6

## Node only

For a node only install, install the needed python modules:

```
pip3 install -r requirements-node.txt
```

You may want to edit your config, or just run the node with defaults, and let it sync. Here, I first run a screen, then run the node inside the screen  
```
screen -S NODE
python3 node.py
```
Then no matter what happens to the ssh connection, I can find my running node when I need to with a `screen -x NODE`.  
> `ctrl-a d` is used to (d)etach from a running screen.

Let your node sync. It will download the bootstrap ledger from the website, then go crazy fetching backlog of blocks. That's ok, give him some time.

## Node and wallet

The wallet does connect to a node.  
In order to run your wallet you used to also need a running node.  
Nowadays, it's not needed anymore. The light wallet can connect to an online node.  
It will try to connect to your local node first, then try online servers. That is, you don't need anymore a node nor a complete chain sync to run and use your wallet.

Here are the python modules for the node again, from previous paragraph
```
pip3 install -r requirements-node.txt
```

And here are the extra modules currently needed for the wallet:
```
pip3 install -r requirements.txt
```

If you want to run Bismuth-wallet on Ubuntu 18.04, you additionally need to install
```
sudo apt install python3-tk
```

If you want to test wallet_async.py (should perform better, due to non blocking behaviour when wallet gets information form node or wallet-server), you need to add:
```
pip3 install tornado
```

## OS config

### limits
On the node box, be sure to have enough files limits (replace root by the user the node will run under)
```
nano /etc/security/limits.conf
root soft nofile 65535
root hard nofile 65535
```

```
nano /etc/sysctl.conf
```
Append:  
```
fs.file-max = 100000
```
then apply the settings
```
sysctl -p
```

### Time

make sure your time is network synced
```
timedatectl
```
Should say "Network time on: yes"  
> if network sync is not active, `timedatectl set-ntp on`

### TCP Settings
Low latency won't do harm
```
echo 1 > /proc/sys/net/ipv4/tcp_low_latency
```

### Locales
> If your install complains about locales only:
```
export LC_ALL="en_US.UTF-8"
export LC_CTYPE="en_US.UTF-8"
sudo dpkg-reconfigure locales
```

## Node and wallet on distinct hosts

See config.txt, edit "light_ip" with a list of ip:port to try to connect to.
The defaults are safe.

## Config file

TODO - dedicated page

## Common errors

(thanks to @cryptonoob42)

### Exception in node:  
`peer_ip = s.getpeername()[0]`  
`TypeError: 'NoneType' object is not subscriptable`

remove python3-socks via apt, then upgrade pysocks via pip to version 1.6.8.

### ImportError: No module named 'PIL.ImageTk'

One way of fixing this (on Ubuntu) is to run  
`sudo apt install python3-pil.imagetk`  
or just update pillow from pip to version 5.1.0 
`pip3 install --upgrade pillow`

### Older modules

Make sur you don't use PIL (outdated)
`pip3 remove PIL`
neither pyCrypto (outdated, replaced by pycryptodome)
`pip3 remove PyCrypto`

