## Load Balancer:

The load balancer distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones.

### Network LB

NLB operates at layer 4, it supports for network based routing and it route the tcp/udp/tls traffic, static IPs.

1) Launch more then one server on EC2 Dashboard like Server-A and Server-B.

![image](https://user-images.githubusercontent.com/48147995/225862324-4e06aef0-9f97-4e1f-9861-693b77f531dc.png)

2) Install nginx on the launched servers.
````sh
[root@ip-192-168-1-13 ~]# sudo yum install nginx -y
[root@ip-192-168-1-13 ~]# service nginx start
````
