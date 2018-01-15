# Bismuth Nodes configuration

## Think Twice

You may want to run a node for 2 reasons
- A/ To connect your wallet to, on your local machine
- B/ To be part of the network and help bismuth grow and be stable

B/ Needs good hardware, some technical background, and a commitment to maintain that node.  
You will have to check it's logs, update when a critical release is out, and mitigate issues you *will* face.

If you are not ready to do taht, or have no idea how to do, please do not.

## Config and config_custom.txt

> There is a general misunderstanding and bad use of config.txt.

*config.txt* is part of the distro, will be updated with new releases, and should NOT be edited.  
(it will be overwritten by next update, that may include extra config lines)  

If you need to tune some setting, you create a `config_custom.txt` and in this one, and this one only,
that won't be touched by updates, you can add your custom settings.  
Only Add the line(s) you need to change, no need to copy all from config.txt

## Node requirements

Running a Bismuth node on a low end server will do more harm than good.
An SSD is more than welcome to avoir databases lock and good response time.

4 cores are enough.

See this (old but still ok) doc about setting up some OS settings.
https://EggPool.net/pdf/bismuth-open-files.pdf

## Config items

### What does the setting ‘nodes_ban_reset’ means exactly?
Reset banlist if you have less than node_ban_reset active connections
