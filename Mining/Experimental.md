# Experimental miner

Some of you may use the experimental branch of the miner.  
In general it gives some more hash, but is not considered stable enough to be production ready, so support is limited.

It's available for Windows And linux, ask @EggdraSyl via PM if you want to give it a try

This doc only concerns this experimental Miner "EggMinerOpenCl".

Latest is 210b.

## Config file

Main config file is EGGMinerOpenCL.yaml  
Some params may appear both in .yaml file and on the command line. In that case, the command line takes precedence.

## The bismuth.bat / Bismuth.sh

This is the script to edit and run.   
It runs the miner within a loop, so the miner is restarted should it crash or close itself.

## The .Bat (command line) params 
Obvious params are not detailled, see sample file.

`-r 15`  
reset gpu every 15 minutes
You can let that one to 60, reseting too frequently may lead to more issues than solutions.

`-R 60`
close the miner every 60 minutes.
This avoids stuck GPUs and potential memleaks. With this version, it should be there with -R 60 or -R 120.

`-c`
Use clear hostname as workername, instead of hostname hash.


## The yaml config params 

TODO
