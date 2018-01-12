# Mining in the cloud with Amazon
(On EggPool.Net)

WIP

## Fast overview for users of Amazon EC2

- Create a P3 instance with the following image: ami-ee2c7594  
(AMI Name is Bismuth EggPool Miner 2.043)  
currently only in us-east-1, you may need to copy the image to other regions if needed.

- Connect to your instance (it's an ubuntu based image) via ssh  
`ssh ubuntu@ip.of.your.box`

- Edit the miner config with your BIS address:  
`nano ~/EggMinerGpuLin2/miner.txt`

- Restart the miner service  
`sudo service miner restart`

- Check the output  
Use `tmux a` to see the miner output

## Step by Step with snapshots

(coming)
