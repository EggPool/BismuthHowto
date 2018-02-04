# Overclocking Nvidias on Linux

## Underpowering
EggdraSyl  
`sudo nvidia-smi -pl 200` will set power limit to 200 w for instance.  
Then you may need some overclocking to keep a good hashrate when underpowering.
(coming)

masterminer  
That's great, with that command how do I specify a specifc GPU?

EggdraSyl  
`nvidia-smi -pl 200 -i 0` for the first one  
`nvidia-smi -pl 200 -i 1` for the 2nd one  

## Overclocking

coolbits need to be activated in xorg.conf to enable overclocking

`sudo nvidia-xconfig -a --cool-bits=31`
Then reboot or just logout/login to restart X11.
Coolbits = 31 allow to play with fans as well.

Then you can use `nvidia-xsettings` GUI or set that via shell script

## Sample Script

Here is a sample script you can run at boot.  
It's a real script I use on a 6x1060 GPU rig mining Bismuth.

```
#!/bin/bash

# Set persistence mode
sudo nvidia-smi -pm 1

# Set default power limit
sudo nvidia-smi -pl 80

# Give more to the first GPU (display)
sudo nvidia-smi -i 0 -pl 90
#sudo nvidia-smi -i 1 -pl 80
#sudo nvidia-smi -i 2 -pl 80
#sudo nvidia-smi -i 3 -pl 80
#sudo nvidia-smi -i 4 -pl 80
#sudo nvidia-smi -i 5 -pl 80

# sets leds to 10%
nvidia-settings -a GPULogoBrightness=10

# Set performance mode to 0
# Since we limit power, performance mode only consumes more when not mining.
# Does not give extra Hash.
nvidia-settings -a '[gpu:0]/GPUPowerMizerMode=0'
# This is for first GPU
nvidia-settings -c :0 -a '[gpu:0]/GPUMemoryTransferRateOffset[2]=0'
nvidia-settings -c :0 -a '[gpu:0]/GPUMemoryTransferRateOffset[3]=0'
nvidia-settings -c :0 -a '[gpu:0]/GPUGraphicsClockOffset[2]=150'
nvidia-settings -c :0 -a '[gpu:0]/GPUGraphicsClockOffset[3]=150'

nvidia-settings -a '[gpu:1]/GPUPowerMizerMode=0'
nvidia-settings -c :0 -a '[gpu:1]/GPUMemoryTransferRateOffset[2]=0'
nvidia-settings -c :0 -a '[gpu:1]/GPUMemoryTransferRateOffset[3]=0'
nvidia-settings -c :0 -a '[gpu:1]/GPUGraphicsClockOffset[2]=150'
nvidia-settings -c :0 -a '[gpu:1]/GPUGraphicsClockOffset[3]=150'

nvidia-settings -a '[gpu:2]/GPUPowerMizerMode=0'
nvidia-settings -c :0 -a '[gpu:2]/GPUMemoryTransferRateOffset[2]=0'
nvidia-settings -c :0 -a '[gpu:2]/GPUMemoryTransferRateOffset[3]=0'
nvidia-settings -c :0 -a '[gpu:2]/GPUGraphicsClockOffset[2]=160'
nvidia-settings -c :0 -a '[gpu:2]/GPUGraphicsClockOffset[3]=160'

nvidia-settings -a '[gpu:3]/GPUPowerMizerMode=0'
nvidia-settings -c :0 -a '[gpu:3]/GPUMemoryTransferRateOffset[2]=0'
nvidia-settings -c :0 -a '[gpu:3]/GPUMemoryTransferRateOffset[3]=0'
nvidia-settings -c :0 -a '[gpu:3]/GPUGraphicsClockOffset[2]=150'
nvidia-settings -c :0 -a '[gpu:3]/GPUGraphicsClockOffset[3]=150'

nvidia-settings -a '[gpu:4]/GPUPowerMizerMode=0'
nvidia-settings -c :0 -a '[gpu:4]/GPUMemoryTransferRateOffset[2]=0'
nvidia-settings -c :0 -a '[gpu:4]/GPUMemoryTransferRateOffset[3]=0'
nvidia-settings -c :0 -a '[gpu:4]/GPUGraphicsClockOffset[2]=150'
nvidia-settings -c :0 -a '[gpu:4]/GPUGraphicsClockOffset[3]=150'

nvidia-settings -a '[gpu:5]/GPUPowerMizerMode=0'
nvidia-settings -c :0 -a '[gpu:5]/GPUMemoryTransferRateOffset[2]=0'
nvidia-settings -c :0 -a '[gpu:5]/GPUMemoryTransferRateOffset[3]=0'
nvidia-settings -c :0 -a '[gpu:5]/GPUGraphicsClockOffset[2]=160'
nvidia-settings -c :0 -a '[gpu:5]/GPUGraphicsClockOffset[3]=160'
```
