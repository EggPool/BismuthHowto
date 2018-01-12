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

