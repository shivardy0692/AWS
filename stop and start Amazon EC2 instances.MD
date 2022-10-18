## How do I stop and start Amazon EC2 instances at regular intervals using Lambda?
### Short description
To stop and start EC2 instances at regular intervals using Lambda, do the following:

1.    Create a custom AWS Identity and Access Management (IAM) policy and execution role for your Lambda function.

2.    Create Lambda functions that stop and start your EC2 instances.

3.    Test your Lambda functions.

4.    Create EventBridge rules that trigger your function on a schedule.

### Resolution
Note: If you receive a Client error on launch error after completing the following procedure, see When I start my instance with encrypted volumes attached, the instance immediately stops with the error "client error on launch".

Get the IDs of the EC2 instances that you want to stop and start. Then, follow these steps.
### Create an IAM policy and execution role for your Lambda function
1.    Create an IAM policy using the JSON policy editor. Copy and paste the following JSON policy document into the policy editor:
````sh
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:PutLogEvents"
      ],
      "Resource": "arn:aws:logs:*:*:*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "ec2:Start*",
        "ec2:Stop*"
      ],
      "Resource": "*"
    }
  ]
}
````
2.    Create an IAM role for Lambda.
Important: When attaching a permissions policy to Lambda, make sure that you choose the IAM policy that you just created.
### Create Lambda functions that stop and start your EC2 instances
1.    In the Lambda console, choose Create function.

2.    Choose Author from scratch.

3.    Under Basic information, add the following:
For Function name, enter a name that identifies it as the function used to stop your EC2 instances. For example, "StopEC2Instances".
For Runtime, choose Python 3.9.
Under Permissions, expand Change default execution role.
Under Execution role, choose Use an existing role.
Under Existing role, choose the IAM role that you created.

4.    Choose Create function.

5.    Under Code, Code source, copy and paste the following code into the editor pane in the code editor (lambda_function). This code stops the EC2 instances that you identify.
#### Example function code—stopping EC2 instances
````sh
import boto3
region = 'us-west-1'
instances = ['i-12345cb6de4f78g9h', 'i-08ce9b2d7eccf6d26']
ec2 = boto3.client('ec2', region_name=region)

def lambda_handler(event, context):
    ec2.stop_instances(InstanceIds=instances)
    print('stopped your instances: ' + str(instances))
````
Important: For region, replace "us-west-1" with the AWS Region that your instances are in. For instances, replace the example EC2 instance IDs with the IDs of the specific instances that you want to stop and start.

6.    Choose Deploy.

7.    On the Configuration tab, choose General configuration, Edit. Set Timeout to 10 seconds and then select Save.

Note: Configure the Lambda function settings as needed for your use case. For example, if you want to stop and start multiple instances, you might need a different value for Timeout and Memory.

8.    Repeat steps 1-7 to create another function. Do the following differently so that this function starts your EC2 instances:

In step 3, enter a different Function name than the one you used before. For example, "StartEC2Instances".
In step 5, copy and paste the following code into the editor pane in the code editor  (lambda_function):
#### Example function code—starting EC2 instances
````sh
import boto3
region = 'us-west-1'
instances = ['i-12345cb6de4f78g9h', 'i-08ce9b2d7eccf6d26']
ec2 = boto3.client('ec2', region_name=region)

def lambda_handler(event, context):
    ec2.start_instances(InstanceIds=instances)
    print('started your instances: ' + str(instances))
````
Important: For region and instances , use the same values that you used for the code to stop your EC2 instances.

### Test your Lambda functions
1.    In the Lambda console, choose Functions.

2.    Choose one of the functions that you created.

3.    Select the Code tab.

4.    In the Code source section, select Test.

5.    In the Configure test event dialog box, choose Create new test event.

6.    Enter an Event name. Then, choose Create.

Note: You don't need to change the JSON code for the test event—the function doesn't use it.

7.    Choose Test to run the function.

8.    Repeat steps 1-6 for the other function that you created.

Tip: You can check the status of your EC2 instances before and after testing to confirm that your functions work as expected.

### Create EventBridge rules that trigger your Lambda functions

1.    Open the Eventbridge console.

2.    Select Create rule.

3.    Enter a Name for your rule, such as "StopEC2Instances". You can optionally enter a Description.

4.    In Define pattern, select Schedule.

5.    Do either of the following:

For Fixed rate of, enter an interval of time in minutes, hours, or days.
For Cron expression, enter an expression that tells Lambda when to stop your instances. For information on expression syntax, see Schedule expressions for rules.
Note: Cron expressions are evaluated in UTC. Make sure that you adjust the expression for your preferred time zone.

6.    In Select targets, choose Lambda function from the Target drop-down menu.

7.    For Function, choose the function that stops your EC2 instances.

8.    Scroll down and then select Create.

9.    Repeat steps 1-8 to create a rule to start your EC2 instances. Do the following differently:

Enter a name for your rule, such as "StartEC2Instances".
(Optional) Enter a Description, such as "Starts EC2 instances every morning at 7 AM."
In step 5, for Cron expression, enter an expression that tells Lambda when to start your instances.
In step 7, for Function, choose the function that starts your EC2 instances.

url: https://aws.amazon.com/premiumsupport/knowledge-center/start-stop-lambda-eventbridge/#:~:text=To%20stop%20and%20start%20EC2%20instances%20at%20regular,rules%20that%20trigger%20your%20function%20on%20a%20schedule.
