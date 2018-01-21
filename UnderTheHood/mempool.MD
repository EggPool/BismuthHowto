# What is this mempool thing?

Bismuth uses a so called "mempool" as part of its operations.

Mempool is the "temporary storage" for transactions that are not yet in a block.  
Different nodes can have different transactions in their mempool. It's never perfectly synced across the net.  
Then when a miner finds a block, it is supposed to embed transactions in it.

When a node gets a new mined block, it removes the transactions from the block he may have in its mempool.  
(he may not have them, or not all, or not yet, or have more than the liner did not have or did not include).

If there are still tx in mempool, they will continue to sync across the network until embedded in a block.  
There are of course more (checks, bandwith limiting aso...)

This is just the basics.  
Things look simple at first sight, but when you enter into details and cope with real world issue (bandwith, stuffed mempool, 
thousands of small tx, low end nodes....) it's easy do be wrong and do more harm than good with seemingly good simple ideas.
