# Wallet FAQ

## Can i run a node on one of my machines and the wallet on another using lightip?

Sure  
On the node machine, use "allowed" in config.txt to allow the wallet ip to connect  
allowed can be "any" or a list of ips.

***
## How can i use the light wallet?

(June 2018)

In your bismuth-folder is a file called config.txt. It gets adjusted on new releases, but sometimes when we develop new things, some things needed to be adjusted.
for the wallet, the main config-line is "light_ip". This is the line, where all ip-addresses are listed, your wallet tries to connect to.
It looks like this:
- *light_ip=127.0.0.1,bismuth.online:8150,bismuth.live:8150,bismuth.live,66.70.181.150,heatnodes.org*

127.0.0.1 is used, if you are running a node locally (you started node.exe or node.py).

The other addresses are for the "light" purpose, you don't need to run a node, your wallet connects to them and gathers all information it would from a local node.

No worries, your private-keys are on your harddrive, your wallet used them, the contacted servers do not know them and **DO NOT NEED them in ANY CASE**.

The addresses with the Port 8150 are newly developed Wallet-Servers, they should be faster and have more capacities for light-wallets, but they are still in a light-testing phase.
When the address is not reachable, your wallet tries the next in the list.

However, sometimes a node or a wallet-server accepts the connection but has some problems (a normal node with high load for example or a wallet-server, where the attached node has problems),
your wallet is starting but stopping and showing a white window or it is starting but showing zero information (no balance, no actual block, just the info where you are connected to).
Best way is to restart the wallet and if it happens again and you are connected to the same node, delete it from the config-line "light_ip".

Actual Wallet Servers that are running (as mentioned still testing how many wallets they can handle and so on):
* wallet.bismuth.online:8150
* wallet1.bismuth.online:8150
* 46.101.186.35:8150