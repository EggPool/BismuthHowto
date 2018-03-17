# EggminerGpu3

Current test version is v3.001

Not released yet, in alpha test.

# Changelog

* 3.001Lin and Win
* New gen, Testing Version
* More Hashrate, specially on NVidias (+10 to +16% on nvidias, +1% on AMD)
* *No more need of -i 50 for nvidias.*
* Optimization and benchmarking procedure
* Less CPU Usage
* More Eggs

# Optimization

You can stop the miner, then run the optimization procedure.
Windows: "optimize.bat".  
Linux: add `--action=optimize`

It'll take a while but will find the best params for your rig, then save them for the miner.  
(file optis.json)

If you physically change your gpus, you'll need to delete optis.json or reun the optimization.

## What does the optimization do?
it makes a reference measure, then scans all potentially reasonable settings to find the best one.
Does not play with clocks, only algo params.
It stops when it tried all, and save its finding in "optis.json" file.

If you run it with -i 100,0,0,0 for instance, it will only optimize the first gpu.  
(can be usefull if you have 8 identical gpus, its faster, and then you edit optis.json to duplicate found settings)

This optimization not only finds the best raw hashrate, but compensate for gpu run time. It measures a "mhu" (Useful MH/s).  
The longer the gpu runs, the more hash you usually get.  
But the more you risk to give stalled shares.  
This measure takes that into account to optimize a meaningfull setting, not just the best displayed hash rate, but the one that will give you the more shares.

# Benchmarking

add `--action=benchmark`  
If you run it with -i 100,0,0,0 for instance, it will only benchmark the first gpu.  
Reports hashrate and mhu for the current setting.  
Usefull if you xant to try different clocks settings from a script to find the best one.


# Optionnal Command Line params
run `./EggMinerGpuLin3 -h` to see available switches.
  
  * -a ADDRESS, --address ADDRESS  
  Mine to that BIS address
  * -n NAME, --name NAME  
  Use a specific worker name
  * -v                 
  Verbose (for debug)
  * -c, --clear           
  Use clear hostname as Worker name
  * -d DELAY, --delay DELAY                         
  Ms to wait between rounds. Lower hash but easier on GPU (not used)
  * -R MIN, --relaunch MIN  
  close cleanly after MIN minutes, to allow for a clean restart  
  720 or 1440 is safe.
  * -i INTENSITY, --intensity INTENSITY  
  GPU intensity, from 0 to 100 (you can list for each gpu)
  * -f damping_factor. 0 to 90  
  Nvidia damping factor. Can be 0 for AMD only. Default 80 if there is at least a Nvidia GPU
  * -0, --gpu0           
  Go Easier on GPU#0 (display - not needed)

# What to use for damping factor?
- AMD Only: use  or 50
- Nvidia: begin with default of 80. If your cpu is really overloaded, raise to 85 or 90.  
  If your CPU still has free cycles, you can try to lower a buit (70 or 60 min) and see if it gives you more hash (but it will eat more cpu).

# What about more hash for AMD?

I focused on nvidia first. I thought it would benefit to AMD too, but it's the opposite.  
what makes nvidia faster slows AMD down. So I'll do it in 2 steps. There is still room for improvement.

# Known bugs

-i 100 doesn’t work, still sets i to 50
I had to specify the comma separated list 100,100,100 etc to get the GPUs to 100 intensit

readme.txt not up to date in linux archive

bug in bismuth.bat, it should read `:run` and not `run:`

possible bug in bismuth.sh

Some "INVALID COMMAND QUEUE" crashes, investigating.

# Some features from experimental branch are missing

* Missing the colored lines of 2.3.4
* no json status
* no alternate directory

# Stability reports

## Linux OK
Ubuntu 16.04, nvidia 387.34 (stable for 2 days +)
Ubuntu, nvidia 390.25 (stable for 2 days)

## Windows OK
Win 10 Pro x64 build 16299, NVidia driver 390.77  
Win 8.1 Version 6.3.9600 - 391.01 drivers - 6xgtx 1070 (about one crash per hour)  
Win 10 16299, Nvidia 391.01, GPU +150 on 1060s and +120 on 1080tis, PLs at 90  

## Windows Ko
Win 10 Pro build 16299, NVidia driver 390.65 - Gtx1060 oc +150/0 - crash twice per hour
