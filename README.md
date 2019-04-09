# TL-WN725N_Linux_Driver
Initial version of driver's code was got from page https://www.tp-link.com/us/support/download/tl-wn725n/v3/ 
 (https://static.tp-link.com/2018/201805/20180521/TP-Link_Driver_Linux_series7_beta.zip)

Operating System: Linux (kernel 2.6.18 ~ 4.4.3)
1. For TL-WN722N v3/TL-WN725N v3.
2. For Linux kernel 2.6.18 ~ 4.4.3.
3. Support monitor mode on ubuntu and mint.
4. This is a beta version; unknown bugs may still exist. The formal version is coming soon.

As I need it to work on Ubuntu 16.04 I fix the code for kernel **4.15.0-45-generic**. The fixed driver worked on this kernel.

You could use this patch  at your own risk.

# Compile the Driver 
Use Terminal to go to the driver directory and run the following commands to compile the driver: 

$ make clean

$ make

After compiling, you can see a name of the chip.ko file is stored in the directory of the driver.

# Load the Driver
Here we show the 8188eu.ko wireless driver loading process as an example. Run the following command to load the driver: 

$ sudo cp 8188eu.ko /lib/modules/[kernel version]/kernel/drivers/net/wireless/  
    #[kernel version] is the directory name of the system kernel version

$ sudo depmod –a 

$ sudo modprobe 8188eu.ko 
 
Or directly use insmod to load the driver: 

$ sudo insmod 8188eu.ko 
 
After loading the driver, run the following command to check if the driver is successfully loaded:

$ lsmod
