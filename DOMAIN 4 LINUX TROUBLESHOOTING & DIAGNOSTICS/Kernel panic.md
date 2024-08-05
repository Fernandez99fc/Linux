# Error: Kernel panic not syncing

![u4aa3](https://github.com/user-attachments/assets/d386f7f4-38e0-4e7f-9f3a-0896e02c7580)

In my case, I forgot the root password and at the same time was experiencing the kernel panic so it was challenging.

So I booted up, pressed esc in the grub menu, select advanced, at the end, press e to edit and:
FIND THE LINE THAT STARTS WITH "LINUX",  SPECIFIES THE BOOT PARAMETER.

LOCATE "RO QUITE", REPLACE "RO" TO "RW" AND ADD /BIN/BASH.

"RW INIT=/BIN/BASH".

press ctr+x to boot again.

After resetting, we are back to the kernel panic. Then we need to boot into recovery mode by going to advanced again. Once we are in the root user account, we do:
- mount -o remount,rw / - to remount the whole filesystem.
- mkinitramfs -o /boot/initrd.img-$(uname -r) or your current version, enter manually.
![Screenshot (104)](https://github.com/user-attachments/assets/f28cd506-1e9a-411c-9226-7389a992fe67)

- update-grub
![Screenshot (106)](https://github.com/user-attachments/assets/ce6067e2-93d9-47f8-b996-32038597209a)

reboot -f

OR

go to turn on or off windows features, look for virtual machine platform and uncheck. reboot the system and start kali. It should work.

OR 

check if you are out of space and delete some stuffs(This was my case)





