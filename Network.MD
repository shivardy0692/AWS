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
