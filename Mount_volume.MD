## Identify and format the disk with xfs

###### i have craeted volume with 4 GB and attached to ec2.

###### login to ec2 instace 

###### Run the below command to list the disk you attached to your instance.

![image](https://user-images.githubusercontent.com/48147995/195830902-3486112a-80b0-4432-8933-015679fc4f9e.png)

###### Check if the volume has any data using the following command.
````sh
file -s /dev/xvdb
````
###### If the response shows “/dev/xvdb: data”, it means your volume is empty.

###### Format the volume to xfs filesystem.
````sh
mkfs.xfs  /dev/xvdf
````
###### create one directory.
````sh
mkdir mount_volume
````
###### Mount the file system on the created directory.
````sh
mount /dev/xvdf mount_volume
````
###### Data should be there after reboot using below command.
````sh
blkid
````

###### To Check file system 
````sh
vi /etc/fstab
````
###### We shiuld check unmounted devices using below command.
````sh
mount -a
````

###### Check disk space
````sh
df -hT
````

![image](https://user-images.githubusercontent.com/48147995/195832785-0e91eddb-5026-473c-8156-d194d9622a9f.png)
