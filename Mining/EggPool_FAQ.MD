# EggPool FAQs

(WIP)

## When are we paid?
Auto payouts are run twice a day, for balances > min payout.
- 9h17 UTC
- 21h17 UTC

(Then there may be some delay for hundreds of transactions to go through)

## What is the min payout?
- Default payout is 10 BIS
- You can ask to lower your payout to 1BIS minimum (email, slack, twitter...)
- You can see your current payout on your miner dashboard page

## What are rounds?

A round is one hour.  
Every hour, we count the blocks we found, the shares of each miner, then store that and reset for the next round.  
At the beginning of a round, you will then see a hashrate of 0, 0 blocks found, aso : it's ok, not enough info yet to tell.  
At the end of a round, the picture is more complete.

Display is delayed of about 5 minutes.
So, at O'6, you See data from O'0 to O'5, and so on.

## What is "immature?"

With the blockchain technology, there may be rollbacks, orphans blocks.  
Hence, a block we found can disappear after a while. That's not frequent, but may happen.  
So, we have to be sure what we gained is solid before sharing.  

So, immature are the shares from previous round, that we did not add to your balance yet.
They will be added at the end of the round.

## I just found a share but it's not on my dashboard?

- Display is updated every 5 minutes with a 1 minute delay. A share found at 15h12 will only be visible at 15h16 for instance.
- sometimes, you can send a stalled share. You were mining a block, but by the time you find a share and send it, another miner found the block, hence the block changed and your share is no more valid.  
this happens for everyone, so on average, it evens out. Of course, if you only have stalled shares, then there is an issue with your miner.

## What are shares @81 and shares @94?
