# Experimental miner

Some of you may use the experimental branch of the miner.  
In general it gives some more hash, but is not considered stable enough to be production ready, so support is limited.

It's available for Windows And linux, ask @EggdraSyl via PM if you want to give it a try

This doc only concerns this experimental Miner "EggMinerOpenCl".

Latest is 210b.

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

`-r 15`  
reset gpu every 15 minutes
You can let that one to 60, reseting too frequently may lead to more issues than solutions.

`-R 60`  
close the miner every 60 minutes.
This avoids stuck GPUs and potential memleaks. With this version, it should be there with -R 60 or -R 120.

`-c`
Use clear hostname as workername, instead of hostname hash.


## The yaml config params 


`damping`  
This should be 60 for nvidias. Can be 0 *for AMD Only*.  
Use 0 for nvidias and you will use 100% cpu and crash.  
Double check this one!

WIP

## Windows, missing DLL

You may need visual C++ 2010 redistributable, here is latest version from Microsoft:  
https://www.microsoft.com/en-us/download/details.aspx?id=26999&tduid=(509a61115e4c36694181baac754e734b)(266696)(1544997)(06-3589464-11-0000000)()

