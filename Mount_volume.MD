## Mount EBS Volume to EC2 instace

###### step 1) i have craeted volume with 4 GB and attached to ec2.

###### step 2) login to ec2 instace 

###### step 3) execute cmd on termonol -- lsblk

![image](https://user-images.githubusercontent.com/48147995/195830902-3486112a-80b0-4432-8933-015679fc4f9e.png)

###### step 4) execute -- mkfs.xfs  /dev/xvdf

###### step 5) create one empty directory ex: mkdir mount_volume

###### step 6) execute -- mount /dev/xvdf mount_volume

###### step 7) execute -- blkid (data should be there after reboot)

###### step 8) execute -- vi /etc/fstab

###### step 9) execute -- mount -a (we shiuld check unmounted devices)

###### step 10) execute -- df -hT  

![image](https://user-images.githubusercontent.com/48147995/195832785-0e91eddb-5026-473c-8156-d194d9622a9f.png)
