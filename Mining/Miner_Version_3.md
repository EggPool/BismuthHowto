# EggminerGpu3

Current test version is v3.001

Not released yet, in alpha test.

# Changelog

* 3.001Lin and Win
New gen, Testing Version
More Hashrate, specially on NVidias
No more need of -i 50 for nvidias.
Optimization and benchmarking procedure
Less CPU Usage
More Eggs

# Optimization

You can stop the miner, then run the optimization procedure.
Windows: "optimize.bat".  
Linux: add --action=optimize

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
The longuer the gpu runs, the more hash you usually get.  
But the more you risk to give stalled shares.  
This measure takes that into account to optimize a meaningfull setting, not just the best displayed hash rate, but the one that will give you the more shares.

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
  * -0, --gpu0           
  Go Easier on GPU#0 (display - not needed)



# Known bugs

-i 100 doesn’t work, still sets i to 50
I had to specify the comma separated list 100,100,100 etc to get the GPUs to 100 intensit

readme.txt not up to date in linux archive

bug in bismuth.bat, it should read `:run` and not `run:`

possible bug in bismuth.sh
