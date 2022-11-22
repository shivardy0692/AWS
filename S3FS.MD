## S3 File Storage

#### Step-1:- If you are using a new centos instance. Update the system.
```sh 
yum update all
```
#### Step-2:- Install the dependencies.
```sh 
sudo yum install automake fuse fuse-devel gcc-c++ git libcurl-devel libxml2-devel make openssl-devel
```
#### Step-3:- Clone s3fs source code from git.
```sh 
git clone https://github.com/s3fs-fuse/s3fs-fuse.git
```
#### Step-4:- Now change to source code  directory, and compile and install the code with the following commands:
```sh 
cd s3fs-fuse
./autogen.sh
./configure --prefix=/usr --with-openssl
make
sudo make install
```
#### Step-5:- Use below command to check where s3fs command is placed in O.S. It will also tell you the installation is ok.
```sh 
which s3fs
```
#### Step-6:- Getting the access key and secret key.
```sh 
You will need AWS Access key and Secret key with appropriate permissions in order to access your s3 bucket from your EC2 instance. You can easily manage your user permissions from IAM (Identity and Access Management) Service provided by AWS. Create an IAM user with S3 full access(or with a role with sufficient permissions) or use root credentials of your Account. Here we will use the root credentials for simplicity.

Go to AWS Menu -> Your AWS Account Name -> My Security Credentials. Here your IAM console will appear. You have to go to Users > Your Account name and under permissions Tab, check whether you have sufficient access on S3 bucket. If not, you can manually assign an existing  “S3 Full-Access” policy or create a new policy with sufficient permissions.

Now go to Security Credentials Tab and Create Access Key. A new Access Key and Secret Key pair will be generated. Here you can see access key and secret key (secret key is visible when you click on show tab) which you can also download. Copy these both keys separately.

Note that you can always use an existing access and secret key pair. Alternatively, you can also create a new IAM user and assign it sufficient permissions to generate the access and secret key.
```
#### Step-7 :- Create a new file in /etc with the name passwd-s3fs and Paste the access key and secret key in the below format .
```sh 
touch /etc/passwd-s3fs
vim /etc/passwd-s3fs
Your_accesskey:Your_secretkey
```
## Step-8:- Change the permission of file
```sh 
sudo chmod 640 /etc/passwd-s3fs
```
## Step-9:- Now create a directory or provide the path of an existing directory and mount S3bucket in it.
```sh 
mkdir /mys3bucket
s3fs your_bucketname -o use_cache=/tmp -o allow_other -o uid=1001 -o mp_umask=002 -o multireq_max=5 /mys3bucket
#### reboot
vi /etc/s3fs
s3fs#ecc-hcm-archieve-27-02-2022 /export fuse _netdev,allow_other,dbglevel=info,url=https://s3.amazonaws.com,iam_role=auto,multireq_max=500 0 0
```

ref url: https://cloudkul.com/blog/mounting-s3-bucket-linux-ec2-instance/
         https://upcloud.com/resources/tutorials/mount-object-storage-cloud-server-s3fs-fuse
