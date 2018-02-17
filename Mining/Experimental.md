# Experimental miner

Some of you may use the experimental branch of the miner.  
In general it gives some more hash, but is not considered stable enough to be production ready, so support is limited.

It's available for Windows And linux, ask @EggdraSyl via PM if you want to give it a try

This doc only concerns this experimental Miner "EggMinerOpenCl".

Latest is [Version231](https://github.com/EggPool/EggMinerGpu/releases/tag/231).

## Config file

Main config file is EGGMinerOpenCL.yaml  
Some params may appear both in .yaml file and on the command line. In that case, the command line takes precedence.

Lines beginning with a `#` are comment, and so are ignored.

Params are like  `param_name: param_value`

Lists are  
```
list_name:
-  item1
-  item2
```


## The bismuth.bat / Bismuth.sh

This is the script to edit and run.   
It runs the miner within a loop, so the miner is restarted should it crash or close itself.

## The .Bat (command line) params 
Obvious params are not detailled, see sample file.

`-R 120`  
close the miner every 120 minutes.
This avoids stuck GPUs and potential memleaks. With this version, it should be there with -R 120 to -R 1440  
(restart at least once per 24h)

`-c`
Use clear hostname as workername, instead of hostname hash.


## The yaml config params 


`damping`  
This should be 60 for nvidias. Can be 0 *for AMD Only*.  
Use 0 for nvidias and you will use 100% cpu and crash.  
Double check this one!
*For AMD, recommended param is 50*  
*For Nvidia, current recommendation is 80*  
On rigs with many GPUs, 85 or 90 may give better result and less CPU usage.

`logdirectory`  
The folder where to store logfiles and json status.  
By default, "Log".  Can be on another disk, or use /dev/null to deactivate any file writing (*not* recommended)

`intensity` (also -i on command line)  
100 for AMD gpus, 50 for nvidias. Some nvidias (but not 1080 nor 1080ti) may support 100.  
Only use 50 or 100. Other values are likely to give worse results.  
You can use `0,50,100,100` to disable the first gpu (should it be the mobo gpu), 50 for the gpu #1 and 100 for the remaining 2 gpus.  
See https://github.com/EggPool/BismuthHowto/blob/master/Mining/Common_Issues.MD

`gpu0`  
Default false. Set to true to ease the load on gou #0 if this is also your main display.

`delay`  
Default 0.  
Ms to wait between rounds. Lowers hash but easier on GPU. No real need to use that.

`servers`  
May be used for custom servers.  Contact eggpool if you have a large mining operation (hunders rigs, not gpus, or more) and need private servers.

`worksize`  
For advanced tuning only. Leave that untouched (commented out, so it uses best default param)

`numhashes`
If the status.json shows a long time for gpu runs, you can limit numhashes here after writing down what the defautl was.  
Leave that commented out by default for auto tuning.

## The logs

The log file may help to diagnose issues. It will be required for support.

## Json Status

This version writes and updates a `status.json` file in its Log directory.
This file can be used to monitor the miners.  

Here is a real json status for a 4 gpus rig:
```
{
  "Timestamp": 1518888489,
  "Started": "2018-02-17 16:07:09",
  "UpTime": 141,
  "BismuthAdress": "fde0a6765bca9dc56bbbed4c771f13909d8cdf2cf5d5b4bfc16c8b34",
  "MinerName": "9f3261a2c590ba9e",
  "Version": "2.3.1+linux",
  "PoolDiff": 94,
  "GPUS": [
    {
      "Name": "GeForce GTX 1070 Ti",
      "HashRate": 1102,
      "TimeGPU": 2744,
      "WorkSize": 19456,
      "NumHashes": 155648
    },
    {
      "Name": "GeForce GTX 1070",
      "HashRate": 1051,
      "TimeGPU": 1793,
      "WorkSize": 15360,
      "NumHashes": 122880
    },
    {
      "Name": "GeForce GTX 1070",
      "HashRate": 993,
      "TimeGPU": 1899,
      "WorkSize": 15360,
      "NumHashes": 122880
    },
    {
      "Name": "GeForce GTX 1070 Ti",
      "HashRate": 1223,
      "TimeGPU": 2474,
      "WorkSize": 19456,
      "NumHashes": 155648
    }
  ],
  "Total": {
    "HashRate": 4.36,
    "OkShares": 23,
    "Shares81": 1352,
    "Shares81PerMin": 9.588652482269504,
    "SharesPerMin": 0.16312056737588654
  }
}
```

Units are:  
- Uptime: minutes
- Individual Hashrate: MH/s
- TimeGPU: ms
- Total Hashrate: GH/s

For instance, you can monitor "Shares81" and check the number moves.


## Windows, missing DLL

You may need visual C++ 2010 redistributable, here is latest version from Microsoft:  
https://www.microsoft.com/en-us/download/details.aspx?id=26999&tduid=(509a61115e4c36694181baac754e734b)(266696)(1544997)(06-3589464-11-0000000)()


## Changelog 

# 2.3.1.


