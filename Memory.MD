ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head

````sh
Swap Memory (Linux): 
swapon --> we will get swap file path.
swapoff /swap file path --> will turn-off swap.

#### Create swap:
$ dd if=/dev/zero of=/swapfile bs=1M count 4096 status=progress
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile

vi /etc/fstab
/swapfile   none   swap   sw   0    0  
````
             
