# LINUX: How to have the miner auto start on boot

## Option 1: Write a proper service
Under Ubuntu, you can have a service file that will autostart and restart your miner when needed.  
(Doc upcoming)

## Option 2: Simple crontab

### 2a - start script

This is a simple script that will run the miner from within a loop, in a screen command.  
Pre-requisite : screen  
`sudo apt install screen`

The script, `~/start_bismuth.sh`: 
```
#/bin/sh

# Here you can auto setup gpu config commands, 
# see https://github.com/EggPool/BismuthHowto/blob/master/Mining/Linux_NVidia_OC_Underpower.MD

# Give it some time to be ready
sleep(5)

screen -d -S miner -m bash -c "cd /where/your/miner/files/are;./bismuth.sh"
```

now, `chmod +x ./start_bismuth.sh` and test it.  
It will run the miner in a screen, so you can see the output from anywhere, local or via ssh.  
use `screen -x miner` to attach to that screen, and where you're in, ctrl-a-d to detach.

### 2b - Auto run at boot

edit your crontab and add a @boot entry:

`crontab -e`  
If your script is in you home dir, add a line like  
`@boot ~/start_bismuth.sh`

### 2c - more goodies

In that autostart script, you can also  open terminal windows.  
Let's say you want to have a look at your nvidia gpus, add these:  
```
# Run Processes
screen -d -S info -m bash -c "watch -n 2 /usr/bin/nvidia-smi"
sleep 1
mate-terminal -e "screen -x info" --geometry=82x48+0+0 &
```

This will run and update nvidia-smi every 2 seconds, in a screen, then open a terminal window and auto attach to that screen.

