# Bismuth Wallet Issues?

## Common issues

### "Wallet cannot connect to the node"
"check config.txt for light_ip"

You wallet has to be connected to a node.  
By default, the node it connectes to is your own machine, 127.0.0.1

So, you have to also run the node on your machine, then your wallet will connect.

### After I hit send and confirm, nothing happens
- Wait a little bit.
- still nothing? check your connected to the node, and node is sync
- close wallet, relaunch node, relaunch wallet

### I've sent a transaction from/to ??? but it doesn't show?
- check ledger query at http://bismuth.online
- check that a new block is mined after your transaction
- if your transaction is there, is'an issue with the recipent.
- If it's not there, issue with the sender :)


## Sending to Cryptopia

- recipient: paste cryptopia address
- amount: how many BIS to transfer
- data: enter your personal cryptopia code
- no need to tick "message" box
- hit "send" and confirm.

- You can chheck the transaction went through after a while, via http://bismuth.online

### When I try to send my mined bismuths to cryptopia. It says invalid adress
- Double check you didn't paste a space at beginning or end of the address
