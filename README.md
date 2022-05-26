# sync-spoofer-reversal
Public pasted spoofer that claims to work on eac be and vgk, but i have not found this to be true.

## Installation Procedure
1. Run loader, login, to load the EFI driver it swaps bootmgfw.efi (xerox's method) and pends restart
2. Requires you to uninstall OneDrive and logout of your Microsoft Account
3. Run loader after restart again to get some other pasted driver to map.

## Reversal Procedure
1. The begging is always about checking their protection / virtualization and their own security or anti-vm functionality, it took minutes to find out they have none and the whole loader is in python and obfuscated.
2. Firstly i tried to see how they are loading the efi file and since the process is automatic its using the common method of swapping bootmgfw.efi so it was a easy grab with a small script i wrote to look for changes in the efi partition
3. Then i read in the instructions that i know need to also load a second driver manually. so i made a grabber to fetch the vulnerable and i found out it was being written in temp folder and saw its signed by intel (kdmapper)
4. then for mapper/driver i noticed they don't even map the driver from the loader itself by trying to hook some common kdmapper functions, they put the mapper and driver in a temp folder, map & delete (extremely poor work)
5. lastly i was interested in their hwid system and dissapointed again to find out they run wmic.exe to get the processorid and use that for a hwid lock.

![Mapped Driver](./driver_dump.png)
![Vulnerable Driver](./vulnerable_dumped.png)
![Running Processes](./process_dump.png)
![Hwid Lock](./hwid_lock.png)
![Mapper Dump](./mapper_dump.png)
