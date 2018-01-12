# Overclocking Nvidias on Linux

EggdraSyl  
`nvidia-smi -pl 200` will set power limit to 200 w for instance.  
Then you may need some overclocking to keep a good hashrate when underpowering.
(coming)

masterminer  
That's great, with that command how do I specify a specifc GPU?

EggdraSyl  
`nvidia-smi -pl 200 -i 0` for the first one  
`nvidia-smi -pl 200 -i 1` for the 2nd one  
