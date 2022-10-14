## Steps to install AWS Command Line Interface tools on Windows:

#### Download AWS Command Line Interface installer file from AWS website using a web browser.
````sh
https://awscli.amazonaws.com/AWSCLIV2.msi
````
#### check aws version on cmd

![image](https://user-images.githubusercontent.com/48147995/195788151-d3f4d56a-be3c-456c-9864-166f2f0e75b4.png)

#### Download aws s3 logs on local drive 
````sh
aws s3 sync s3://YOUR_BUCKET .
````
## Steps to install AWS Command Line Interface tools on linux:

#### Step 1) First, update your Ubuntu Linux system and install unzip and curl packages.
````sh
sudo apt update && sudo apt upgrade -y && sudo apt install unzip curl -y
````
#### Step 2) Then download & unzip AWS CLI.
````sh
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
&& unzip awscliv2.zip
````
#### Step 3) Finally, install AWS CLI.
````sh
sudo ./aws/install
````
#### Verify that you can use the AWS CLI by running the following command:
````sh
aws --version
````
