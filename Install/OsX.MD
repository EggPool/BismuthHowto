# How to install the wallet on Mac Os X?

Note: I'm no mac user. I assembled this guide from various feedback. If you are a mac user and can improve or clarify this, please do! Issue a PR and I'll be glad to merge!

This guide only covers the wallet for now.

## Pre-requisites

Python3.5 or later is needed, as well as matching pip.  
For some recent node versions or branches, Python 3.6 may be needed.

You need basic knowledge of your mac, that is opening the terminal and installing an app.

Here is a guide for installing python3.6.  
I'd advise to prefer the homebrew method.  
http://osxdaily.com/2018/06/13/how-install-update-python-3x-mac/

install and Upgrade pip if needed:  
```
sudo easy_install pip 
pip install --upgrade pip
```

Manually install some prerequisites, to make sure we have the latest versions:

```
pip install --upgrade pillow
pip install --upgrade simple-crypt
pip install --upgrade pycryptodomex
```

## Fetch the source files

It's advised to use the releases rather than current git code.  
Current github code may contain untested features and code. 

Head over to the official Bismuth Github repo, releases: https://github.com/hclivess/Bismuth/releases  
Unless you need a specific version, pick the latest one. As for now, this is 4.2.5.3.  
Copy the link of the "Source Code (tar.gz)" file. Mine is https://github.com/hclivess/Bismuth/archive/4.2.5.3.tar.gz

Back to your Ubuntu box, fetch the file where you want it installed, like your home dir, and extract it:
```
cd
wget https://github.com/hclivess/Bismuth/archive/4.2.5.3.tar.gz
tar -zxvf 4.2.5.3.tar.gz
```
It extracts itself under Bismuth-4.2.5.3

## Install the wallet

The wallet does connect to a node.  
In order to run your wallet you used to also need a running node.  
Nowadays, it's not needed anymore. The light wallet can connect to an online node.  
It will try to connect to your local node first, then try online servers. That is, you don't need a node anymore nor a complete chain sync to run and use your wallet.

Here are the modules currently needed for the wallet:

```
pip install -r requirements.txt
```

## Run the wallet

`python wallet.py`

This will create a new "wallet.der" file, in the same dir.  
This is your wallet, backup that file in a safe place.
> If you already have a wallet, place your wallet.der in the dir before running wallet.py



