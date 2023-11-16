ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head

````sh
Swap Memory (Linux): 
swapon --> we will get swap file path.
swapoff /swap file path --> will turn-off swap.

Create swap:
$ dd if=/dev/zero of=/swapfile bs=1M count 4096 status=progress
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile

vi /etc/fstab
/swapfile   none   swap   sw   0    0  
reboot
````
````sh
Control Panel --> All Control Panel Items --> System --> Advanced system settings --> Advanced tab --> edit performance --> visual effects tab (adjust for best appearance) --> advanced tab   
