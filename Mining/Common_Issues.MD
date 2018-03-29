# Common issues mining BIS

## How to deactivate the mobo iGpu ?
## Linking two modules of different data layouts
## How to disable a specific GPU

If you have an iGPU, then the miner may find it and try to mine with it.  
This doesn't work and may crash the miner, so you have to disable this GPU.

*To disable a specific GPU:*
- look at the GPU list at miner launch
- id the number of the gpu
- use `-i` on the command line with a list of intensities instead of just one. 

For instance, if you have the iGPU and then 2 NVidias GPUs, use `-i 0,100,100`  
intensity to 0 for a GPU will disable it completely.


## I'm getting "out of ressources" errors

> Nvidias GPUs?  
- Did you use `-i 50` on command line? (see .bat or .sh)
THIS IS NO MORE NEEDED WITH V3+ Miner. !! -i 50 will mine at 50% hashrate !!

- Are your drivers up to date?
Reinstall even if they are.

> AMD  
- be sure to follow the install procedure and install opencl drivers matching your hardware too
