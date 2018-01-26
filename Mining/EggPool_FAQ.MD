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

## What is "immature?"

With the blockchain technology, there may be rollbacks, orphans blocks.  
Hence, a block we found can disappear after a while. That's not frequent, but may happen.  
So, we have to be sure what we gained is solid before sharing.  

We don't want to give false hope either and display an immature balance then reduce it if a block is rolled back.

So, immature are the shares from pre-previous round, that we did not add to your balance yet.
They will be added to the unpaid balance at the end of the current round.

 ## I just found a share but it's not on my dashboard?

- Display is updated every 5 minutes with a 1 minute delay. A share found at 15h12 will only be visible at 15h16 for instance.
- sometimes, you can send a stalled share. You were mining a block, but by the time you find a share and send it, another miner found the block, hence the block changed and your share is no more valid.  
this happens for everyone, so on average, it evens out. Of course, if you only have stalled shares, then there is an issue with your miner.

## What are shares @81 and shares @94?

Network diff is high. So pool diff is high, too.  
We set it to 94. (where as network diff is > 109 as I write this)  
With a "small" hash power (a few gpus) You may wait a long time (several minutes or hours) to get a single share at that diff. So we also display shares at diffculty 81. They are way more.  
For each share at 94, there are like 100 at diff 81.

So, the miner displays the shares found at diff 81 as a benchmarck, to show it mines.
For 1GH/s, the miner should give you about 2 shares at 81 per minute.  
So, 4GH/S => 8 shares at @81 per minute.

If shares @81 raise, you are minning. Then it's just a question of time (and luck) to get shares @ 94.  
(remember, on average 1 share @ 94 for 100 @ 81)

Only the shares @94 are sent and count. If you do not have enough shares at 94, then you need more GPUs :)

## You are greedy greeny Eggys, why such fees?

> tl;dr : What really counts is what *YOU* get in the end. And you will get more at Egg after our fees than elsewhere, even solo without fee.

We are aware our fees are unusual in crypto world. But, as Bismuth does, we do nothing like the others and prefer from scratch.  
All the pool was written from scratch, and uses an innovative design, with distributed servers all other the world.

When other pools run on a single vps, we have several dedicated servers. Our infra cost is way higher.

Then, our miner outperforms the other ones, and the pool itself, with the same hashrate, finds more blocks than others.  
So it ends us everyone saying  
> "I don"t care the fees, I win more at Egg after the 10% than everywhere else with less or 0 fees".  

Solo miners joined us.  
Big mining farms joined us, because even with 10% fees, they were getting more than mining on their own private pool.  

We really have a lot of such feedbacks.  
So, don't see it as "I give fees to the pool", but as "This pool gives me more".
