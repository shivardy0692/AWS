telnet error for mysql unable to reach connection

If you're getting a "connection timed out" error when trying to connect to a MySQL server using Telnet, it's likely due to one of the following reasons:

MySQL server is not running.
MySQL server is not listening on the default port (3306).
There's a firewall blocking the connection.
Here's how you can troubleshoot:

Check MySQL Service:
bash
Copy code
sudo service mysql status
If it's not running, start the MySQL service:

bash
Copy code
sudo service mysql start
Check MySQL Port:
By default, MySQL listens on port 3306. You can check if it's listening on that port:

bash
Copy code
sudo netstat -tuln | grep 3306
Check Firewall:
Make sure that your firewall allows connections on port 3306.

For Ubuntu with ufw:

bash
Copy code
sudo ufw allow 3306
For CentOS with firewalld:

bash
Copy code
sudo firewall-cmd --zone=public --add-port=3306/tcp --permanent
sudo firewall-cmd --reload
Telnet Connection:
Try to connect using Telnet:

bash
Copy code
telnet <MySQL_Server_IP> 3306
If Telnet establishes a connection, you'll see a blank screen. If not, you'll receive a connection error.

If the Issue Persists:
If you still can't connect, make sure that MySQL is properly configured to allow external connections. By default, MySQL is bound to the loopback interface.

You should check the MySQL configuration file (my.cnf) and ensure that bind-address is either commented out or set to 0.0.0.0.

bash
Copy code
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
conf
Copy code
# bind-address           = 127.0.0.1
Change it to:

conf
Copy code
bind-address           = 0.0.0.0
Then restart the MySQL service:

bash
Copy code
sudo service mysql restart
After this, you should be able to connect to MySQL from remote systems.

Let me know if you need further assistance!
