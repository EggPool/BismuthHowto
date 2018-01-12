# Common issues mining BIS

## How to deactivate the mobo iGpu ?
## Linking two modules of different data layouts
## How to disable a specific GPU

If you have a, iGPU, then the miner may find it and try to mine with it.  
This doesn't work and may crash the miner, so you have to disable this GPU.

*To disable a specific GPU:*
- look at the GPU list at miner launch
- id the number of the gpu
- use `-i` on the command line with a list of intensities instead of just one. 

For instance, if you have the iGPU and then 2 NVidias GPUs, use `-i 0,50,50`  
intensity to 0 for a GPU will disable it completely.


## I'm getting "out of ressources" errors

> Nvidias GPUs?  
- Did you use `-i 50` on command line? (see .bat or .sh)

- Are your drivers up to date?

> AMD  
- be sure to follow the install procedure and install opencl drivers matching your hardware too
