# Specific Windows issues

## The miner can't auto restart, there's a dialog windows I have to click 'close program'

See
- https://social.technet.microsoft.com/Forums/windows/en-US/6025f72e-5bac-4dbd-9992-825828711399/disabling-applicationexe-not-responding-dialog?forum=w7itprogeneral
- https://www.raymond.cc/blog/disable-program-has-stopped-working-error-dialog-in-windows-server-2008/

## Make sure you have the latest Drivers

In doubt, re-install

## Windows update and miner is broken

See https://forums.geforce.com/default/topic/891671/windows-10-build-10576-missing-opencl-dll/

"The fix is to reinstall the driver manually after each Windows upgrade to a new build.  
For some reason, after each upgrade, OpenCL.dll from System32 is lost."
.
## Virtual Memory high enough?

Make it 64000
https://www.geeksinphoenix.com/blog/post/2016/05/10/how-to-manage-windows-10-virtual-memory.aspx
