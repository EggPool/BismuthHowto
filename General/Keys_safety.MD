# Bismuth Keys and safety

Bismuth is a brand new thing. What you think you know with BTC or such is not necessarly true here :)

## Where is my wallet?

The wallet is the ledger (blockchain). It's everywhere, on every BIS node.
You can't "save" your wallet.

## How is my wallet secured?

Your keys are all that is needed to access your wallet.  
They are the important thing to care about.

## So, Where are my keys?

When you run a node for the first time, the node generates a brand new address for you, and a set of private/public key.  
Those are the 3 files in your bismuth dir:
- address.txt
- pubkey.der
- privkey.der

Both .der files you have to take care of. Backup in a secure place, and do not, EVER, give you privkey to anyone.

## And how do I protect them?

Your privkey is only really needed to spent from your account.  
So, if you run a node, use one set of keys (with no BIS) to run your node, then a second set for your wallet, from another dir.

## Cold wallet?

If you want some kind of cold storage, and do not need to spent your BIS right now, you can:  
- run a node on an airgaped machine
- copy the address.txt, you'll need it to send BIS to.
- store on secure offline storage the .der files and matching address.txt
- delete the .der

Then, you'll be able to check your balance at any moment, via http://bismuth.online for instance.  
You will be able to feed your account at any time, just need your address

But you will need to copy your privkey.der to an online machine to spent from it.

## why isn't my pub key also my address?

Told ya, bismuth ain't btc.


## What about encoding my wallet?

TODO


## Paper wallet?

Several people working on it.
