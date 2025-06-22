# Deploying A Node.js Application On AWS EC2
# Testing the project locally
# Clone this project

git clone https://github.com/verma-kunal/AWS-Session.git

# Setup the following environment variables - (.env) file

DOMAIN= ""
PORT=3000
STATIC_DIR="./client"
PUBLISHABLE_KEY=""
SECRET_KEY=""

# Initialise and start the project
npm install
npm run start
# Set up an AWS EC2 instance
Create and log in as IAM user to your AWS Console
Access Type - Password
Permissions - Admin
Create an EC2 instance
Select an OS image - Ubuntu
Create a new key pair & download .pem file
Instance type - t2.micro
Connecting to the instance using SSH
ssh -i instance.pem ubunutu@<IP_ADDRESS>
# Configuring Ubuntu on a remote VM
Updating the outdated packages and dependencies
sudo apt update
Install Git - Guide by DigitalOcean
Configure Node.js and npm - Guide by DigitalOcean
# Deploying the project on AWS
# Clone this project in the remote VM
git clone https://github.com/verma-kunal/AWS-Session.git
# Setup the following environment variables - (.env) file
DOMAIN= ""

PORT=3000

STATIC_DIR="./client"

PUBLISHABLE_KEY=""

SECRET_KEY=""
# Initialise and start the project
npm install

npm run start

NOTE - I edited the inbound rules in the security group of our EC2, in order
to allow traffic from our particular port. 

The project is deployed on AWS and can be accessed using the IPV4 Public Ip address












