CloudWatch: (https://www.youtube.com/watch?v=mIVluHNNioE)

Create an IAM role for cloudwatch and attached given CloudWatchAgentAdminPolicy
````sh
wget https://s3.amazonaws.com/amazoncloudwatch-agent/ubuntu/amd64/latest/amazon-cloudwatch-agent.deb
sudo dpkg -i -E ./amazon-cloudwatch-agent.deb
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard


Log file path:
/var/log/apache2/access.log

default choice: [access.log]
demo-ec2-apache-logs


default choice: [{instance_id}]
apache.access.log

sudo apt-get update -y
sudo apt-get install collectd
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json -s
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a status
````

Aws cloud watch provide real time monitoring of aws resources and customer application running on amazon infrastructure.
Cloud watch stores the data in the form of logs and mertics and event's.

````sh
IAM Roles -> CloudWatchAgentServerPolicy
sudo yum install amazon-cloudwatch-agent -y
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -s -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json
aws console -> cloudwatch -> metrics -> All -> EC2 -> Per-Instance Metrics

sudo yum remove amazon-cloudwatch-agent -y
````

Configure below path for logs:
etc/awslogs/awslog.conf
[/var/log/nginx/error]
datetime-format = %b %b %H : %M : %S
file = /var/log/nginx/error.log
buffer-stream-name = {instance_id}
initial-position = start_of_file
log-group-name = /var/log/nginx/error

# service awslogs start
# service awslogs status

Cloud trail is a service that enable governance, complance, operational auditing and risk auditing of your aws account.
