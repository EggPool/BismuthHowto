# Bismuth Nodes Troubleshooting

## Can't Sync!

Checklist :

- 5658 port is open, no firewall, I can check it's available from the internet. for instance : https://www.yougetsignal.com/tools/open-ports/
- host has its time net synced (important)

Config.txt file:
- config.txt, or config_custom.txt if you use it: I have at least 50 threads `thread_limit=75` is fine.  
- I have nothing in banlist  
- I have bp1.eggpool.net in whitelist (may help getting sync)  

- close and relaunch

If block height does not move, and you are behind (check http://bismuth.online for a live reference)

- close node
- delete peers.txt, and replace by this file (official peers.txt from 4.2.1.9)
https://github.com/hclivess/Bismuth/raw/4.2.1.9/peers.txt  (note: update to more recent file)
- relaunch node

## Innocuous log messages

The following messages are part of normal operation and *NOT* harmuful:  

- handle(1764) Protocol version mismatch: mainnet0014, should be ['mainnet0016', 'mainnet0017']
- worker(2650) Outbound: Disconnected from xx.xx.xx.xx:5658: Unexpected error, received: *
- Outbound: Synchronization with xx.xx.xx.xx finished after: Block found, sending new sync request
- Outbound: Synchronization with xx.xx.xx.xx finished after: No new block, sending new sync request
- digest_block(1356) Check 1: A part of the block is invalid, rejected: Readjusted difficulty too low for block 391212 from xx.xx.xx.xx, should be at least 102.7072271672
- Added 1 warning(s) to xx.xx.xx.xx: Check 1: rejected block (27 / 30)
- Outbound: We have a lower block (467641) than xx.xx.xx.xx
