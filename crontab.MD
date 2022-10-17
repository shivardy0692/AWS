# execute shell script using cronjob
````sh
* * * * *  /bin/sh /root/s3_sync.sh
````

## Cron Job	Command
#### Run Cron Job Every Minute	
````sh
* * * * * /root/backup.sh
````
#### Run Cron Job Every 30 Minutes	
````sh
30 * * * * /root/backup.sh
````
#### Run Cron Job Every Hour	
````sh
0 * * * */root/backup.sh
````
#### Run Cron Job Every Day at Midnight	
````sh
0 0 * * * /root/backup.sh
````
#### Run Cron Job at 2 am Every Day	
````sh
0 2 * * * /root/backup.sh
````
#### Run Cron Job Every 1st of the Month	
````sh
0 0 1 * * /root/backup.sh
````
#### Run Cron Job Every 15th of the Month	
````sh
0 0 15 * * /root/backup.sh
````
#### Run Cron Job on December 1st – Midnight	
````sh
0 0 0 12 * /root/backup.sh
````
#### Run Cron Job on Saturday at Midnight
````sh
0 0 * * 6 /root/backup.sh
````
