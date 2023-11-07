## Load Balancer:

LINUX: we should add loadbalancer subnet ip address to the instance which is in the target group.
port listener: sudo netstat -tunlp
telnet 127.0.0.1 80

result: healthy

Errors: Target --> unhealthy 404
1) we should enable IIS: Press the Windows Key and type Windows Features, select the first entry Turn Windows Features On or Off. Make sure the box next to IIS is checked.
2) windows + r --> inetmgr
3) In the Connections pane, expand the server name, expand Sites, and then click the Web site on which you want to configure the bindings.
4) In the Actions pane, click Bindings...
5) In the Site Bindings dialog box, click Add...
6) Add Site-Bindings as *

````sh
Health Status (unhealthy)
504 Gateway Time-out --> Security group port issue.
Request timed out:
We should configure LB IP to the firewall in the local machine.
````
404 --> curl -lvl https://10.0.0.1/

click windows --> check firewall status --> advanced settings --> add inbound rules
![image](https://github.com/shivardy0692/AWS/assets/48147995/514d19dd-00a9-4c42-8207-7b91f0856974)
![image](https://github.com/shivardy0692/AWS/assets/48147995/70da9239-9b77-4aeb-9b41-3d116785a7aa)
![image](https://github.com/shivardy0692/AWS/assets/48147995/4d5d87d2-d20c-45b5-ac88-58cb96bd250a)

#### Get LB IP from Network Interfaces:

![image](https://github.com/shivardy0692/AWS/assets/48147995/91410c4f-a544-4ee5-805f-21efd73cf574)


The load balancer distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones.

### Network LB

NLB operates at layer 4, it supports network-based routing and routes the tcp/udp/tls traffic, static IPs.

1) Launch more then one server on EC2 Dashboard like Server-A and Server-B.

![image](https://user-images.githubusercontent.com/48147995/225862324-4e06aef0-9f97-4e1f-9861-693b77f531dc.png)

2) Install nginx on the launched servers.

````sh
[root@ip-192-168-1-13 ~]# sudo yum install nginx -y
[root@ip-192-168-1-13 ~]# systemctl start nginx
[root@ip-192-168-1-13 ~]# systemctl enable nginx
[root@ip-192-168-1-13 ~]# systemctl status nginx
````

3) Enable port 80 on the security group that is attached to the launched server in order to enable it.

![image](https://user-images.githubusercontent.com/48147995/225899192-91a29688-b5dc-4612-827e-354469aac5a6.png)

4) Copy and paste the server Public IPv4 DNS on the browser then we will get output.

![image](https://user-images.githubusercontent.com/48147995/225900411-caebde32-1338-4d55-9c5a-6bd81974e29f.png)

![image](https://user-images.githubusercontent.com/48147995/225900598-5b6ee297-f005-46a4-9f9d-538cb90c18bf.png)

5) Create target group.

![image](https://user-images.githubusercontent.com/48147995/225902039-256e1a46-e87f-488a-b241-628b3a819d7e.png)

![image](https://user-images.githubusercontent.com/48147995/225902244-7c9d8eb0-8784-496c-8f9b-7c55d14b2214.png)

![image](https://user-images.githubusercontent.com/48147995/225902612-6f148040-e747-43c0-b6ca-404f2ba1763d.png)

6) Create load balancer.

![image](https://user-images.githubusercontent.com/48147995/225903993-e6079951-9e39-46e9-a055-25709ee24946.png)

![image](https://user-images.githubusercontent.com/48147995/225904482-6809685a-083b-4703-a14a-e3cbdfe0db24.png)

![image](https://user-images.githubusercontent.com/48147995/225905038-4e53b2c2-ea44-475a-af34-41d868795805.png)


