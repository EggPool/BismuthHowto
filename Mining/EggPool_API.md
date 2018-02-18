# Experimental EggPool API

This is experimental, can be ended or evolve without prior notice.  
A qrcode with the direct API url will be added later on.

## Important

Please do *NOT* hammer the service or it will end/you will be blocked.  
> One request per 5 minute is allowed, no more.

## How to access your API?

Go to your dashboard, copy the url  
Ex: `https://eggpool.net/index.php?action=miner&miner=0634b5046b1e2b6a69006280fbe91951d5bb5604c6f469baa2bcd840`

replace `action=miner` by `action=api`, you've got your url:  
`https://eggpool.net/index.php?action=api&miner=0634b5046b1e2b6a69006280fbe91951d5bb5604c6f469baa2bcd840`

## Sample Json output

```
{
  "last_event": 1518975651,
  "BIS": {
    "total_paid": 376.738482479,
    "balance": 1.3327331855433,
    "immature": 0.28556031324285,
    "min_payout": 0
  },
  "round": {
    "hr": 10151,
    "shares": 11,
    "mhr": 9401.8181818182
  },
  "lastround": {
    "hr": 10145,
    "shares": 17,
    "mhr": 10604.235294118
  },
  "workers": {
    "count": 4,
    "detail": {
      "RIG1": [
        4937,
        1518975651
      ],
      "RIG4": [
        10786,
        1518975369
      ],
      "RIG3": [
        7562,
        1518975605
      ],
      "RIG2": [
        2570,
        1518975424
      ]
    }
  },
  "missing": {
    "count": 0,
    "detail": []
  }
}
```

## Info

### BIS

All BIS balance related, same as on your html dashboard

### Round, lastround

Info from accepted shares. HR is the last hashrate (in MH/s) for the round, mhr the average hash rate for the round.  
Same goes for last round.  

One round = 1 hour, A 5 min delay is in place.  
Data of current round at the beginning of a round is empty.

### Workers

Total # of active workers and detail of the workers that sent a status less than 10 minutes ago.  
Worker name => hashrate (Mh/s) , last time seen

### Missing

Same as active workers, but when a previously active worker goes missing (no status for more than 10 minutes).

So you can set an alert if Missing "count" goes positive.

## Mobile monitor app?

PoolWatch seems to work with the API and provides alerts and graphs.  
(not affiliated, no relationship)
[PoolWatch android App](https://play.google.com/store/apps/details?id=com.apaluk.android.poolwatch&hl=fr)
