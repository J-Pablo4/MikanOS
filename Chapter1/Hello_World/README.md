# Chapter 1
## 1.1 Hello World

For this chapter we downloaded an iso image of ubuntu Desktop, which was used to create a virtual machine in VMware. In this virtual machine I installed the application `okteta` which is a binary editor. 
```
$ sudo apt install okteta
```
In the binary editor I wrote the next values:
![](https://github.com/J-Pablo4/MikanOS/blob/master/Chapter1/Hello_World/binary_example.png?raw=true)

To check that the file contents were correct, the following command was used:
```
$ sum BOOTX64.EFI
12430     2
```
After confirming that the file content is correct, the following commands were used to mount the binary on a USB. USB was configured in a FAT format.

```
$ sudo umount /dev/sdb1
$ sudo mkfs.fat /dev/sdb1
$ sudo mkdir -p /mnt/usbmem
$ sudo mount /dev/sdb1 /mnt/usbmem
$ sudo mkdir -p /mnt/usbmem/EFI/BOOT
$ sudo cp BOOTX64.EFI /mnt/usbmem/EFI/BOOT
$ sudo umount /mnt/usbmem
```
Finally, I turned off the virtual machine and restarted the computer so I could `boot from the USB`. As a recommendation from the author, it is requested that the Secure Boot is disabled so that the computer can boot from the USB. The end result is a `Hello World` on the computer monitor.
