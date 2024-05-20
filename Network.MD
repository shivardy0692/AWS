#### Port open for an network error:
````sh
sudo netstat -tuln | grep 3306
sudo ufw allow 3306
sudo ufw allow 'Apache Full'
sudo ufw allow 'Apache'
sudo ufw allow 22/tcp
sudo ufw status

sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf
bind-address           = 0.0.0.0 (public)
sudo service mysql restart
````

#### VPC Peering vs Transit gateway:
````sh
VPC Peering: Network connection between 2 vpc's.
             Two vpc's could be in the same or different aws account.
             Low cost since you need to pay only data transfer.
             There is no bandwidth limited.
             Complete at scale.
             Maximum 125 connections per VPC.
TGW: Using tgw, you can manage multiple connections very easily.
     
````

Check weather the specific port is open on a server:
````sh
telnet ip port (or) Test-NetConnection localhost -port 80
````
Get responce:
curl -lvk https://10.98.113.27/

#### Check Listening Ports with netstat
````sh
sudo netstat -tunlp
The options used in this command have the following meaning:

-t - Show TCP ports.
-u - Show UDP ports.
-n - Show numerical addresses instead of resolving hosts.
-l - Show only listening ports.
-p - Show the PID and name of the listener’s process. This information is shown only if you run the command as root or sudo user.
````
