## Auto backup using Script-Windows to S3 bucket in AWS

1) Download and run the AWS CLI MSI installer for Windows (64-bit):
````sh
https://awscli.amazonaws.com/AWSCLIV2.msi
````
2) To confirm the installation, open the Start menu, search for cmd to open a command prompt window, and at the command prompt use the aws --version command.

![image](https://user-images.githubusercontent.com/48147995/227425844-1812628c-94d7-4560-9581-74b8a0754a0f.png)

3) After this we can configure our secret and access key into it.

4) Next we will create a file of script.

5) In this script we required s3 bucket name & source path means local path like below.
````sh
aws s3 sync file_path s3://bucket_name
````
6) In local machine search box type task scheduler & click and create task.

7) Click on trigger tab & we will schedule the trigger time.

8) Click on action & click new & select script file.

9) So our task schedular is ready..

10) 
