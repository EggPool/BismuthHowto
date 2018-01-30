# Linux Specific issues and FAQ

## Kernel log fills up with errors

I get messages like 

> dmesg
```
[ 1773.436397] pcieport 0000:00:1b.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00dc(Receiver ID)
[ 1773.436399] pcieport 0000:00:1b.4:   device [8086:a2eb] error status/mask=00000001/00002000
[ 1773.436401] pcieport 0000:00:1b.4:    [ 0] Receiver Error         (First)
[ 1773.438355] pcieport 0000:00:1b.4: AER: Corrected error received: id=00dc
[ 1773.438360] pcieport 0000:00:1b.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00dc(Receiver ID)
[ 1773.438363] pcieport 0000:00:1b.4:   device [8086:a2eb] error status/mask=00000001/00002000
[ 1773.438365] pcieport 0000:00:1b.4:    [ 0] Receiver Error         (First)
[ 1773.441376] pcieport 0000:00:1b.4: AER: Corrected error received: id=00dc
[ 1773.441395] pcieport 0000:00:1b.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00dc(Receiver ID)
[ 1773.441398] pcieport 0000:00:1b.4:   device [8086:a2eb] error status/mask=00000001/00002000
[ 1773.441400] pcieport 0000:00:1b.4:    [ 0] Receiver Error         (First)
[ 1773.450745] pcieport 0000:00:1b.4: AER: Corrected error received: id=00dc
[ 1773.450751] pcieport 0000:00:1b.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00dc(Receiver ID)
[ 1773.450754] pcieport 0000:00:1b.4:   device [8086:a2eb] error status/mask=00000001/00002000
[ 1773.450757] pcieport 0000:00:1b.4:    [ 0] Receiver Error         (First)
[ 1773.452416] pcieport 0000:00:1b.4: AER: Corrected error received: id=00dc
```

Workaround is to add pci=noaer to your kernel command line.

* edit `/etc/default/grub` and and add pci=noaer to the line starting with GRUB_CMDLINE_LINUX_DEFAULT. It will look like this:  
  `GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer"`
* run `sudo update-grub`
* reboot

> Some report using pci=nomsi instead of noaer.
