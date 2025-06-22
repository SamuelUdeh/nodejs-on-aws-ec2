# Deploying A Node.js Application On AWS EC2

This project demonstrates how to deploy a simple Node.js application on an Amazon Web Services (AWS) EC2 instance. It covers the full process, from setting up the EC2 environment and configuring security groups, to installing Node.js and running the application, and making it accessible over the internet.

# Prerequisites
- **AWS Account:** An active AWS account.
- **Node.js:** Basic knowledge of Node.js and JavaScript.
- **Git:** Installed on your local machine.
- **SSH Client**: For connecting to your EC2 instance.

## Step 1: Testing the project locally

1. **Clone this project:**

``
git clone https://github.com/SamuelUdeh/nodejs-on-aws-ec2.git
``


2. **Setup Environment Variables:**
   Create a .env file with the following content
   

DOMAIN= ""

PORT=3000

STATIC_DIR="./client"

PUBLISHABLE_KEY=""

SECRET_KEY=""



3. **Initialise and start the project**

``
npm install
npm run start
``


![NodeAWSNPMinstallrun](https://github.com/user-attachments/assets/bf4a091b-6970-4e29-af2b-00ba14840e37)

![LocalTEST](https://github.com/user-attachments/assets/bc415bb9-9a6c-4e1f-a747-206d669cd141)


## Step 2: Launch an EC2 Instance

1. Go to [AWS EC2 Dashboard](https://console.aws.amazon.com/ec2/)
2. Click **“Launch Instance”**
3. Configure:
   - **Name**: `demo-node.js`
   - **AMI**: Amazon Linux 2 or Ubuntu 22.04
   - **Instance type**: `t2.micro` (Free Tier eligible)
   - **Key pair**: Create/download one (e.g., `rent.pem`)
   - **Security Group**:
     - Allow **SSH** (port 22) from *Your IP*
     - Allow **Custom TCP** on port **3000** from *Anywhere* (or Your IP)
4. Launch the instance

![NodeAWSEC2a](https://github.com/user-attachments/assets/a136447d-beef-46a2-ad92-3246f0c4c354)
![NodeAWSEC2](https://github.com/user-attachments/assets/4d8e2a45-b6ec-49e9-8de7-1fc8d2cadb5d)
![NodeProjSG 1](https://github.com/user-attachments/assets/a4924686-0f7c-44d4-9f0e-91a43075bdff)
![NodeProjSG](https://github.com/user-attachments/assets/b21b9ed0-5ba4-45e8-b826-007c385ced7e)

## Step 2: SSH Into EC2

``
chmod 400 rent.pem
``

# For Amazon Linux, use:

``
ssh -i keypair.pem ec2-user@<your-ec2-public-ip>
``

# For Ubuntu, use:

``
ssh -i keypair.pem ubuntu@<your-ec2-public-ip>
``

![NodeEC2SSH](https://github.com/user-attachments/assets/5cd30456-bd19-4c9e-becd-fefe369b6be3)

## Step 3: **Install Node.js on EC2**

**On Amazon Linux:**

``
sudo yum update -y
curl -fsSL https://rpm.nodesource.com/setup_18.x | sudo bash -
sudo yum install -y nodejs
``

**On Ubuntu:**

``
sudo apt update
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
``


![NodeAWSNodeInstall](https://github.com/user-attachments/assets/0e1c6b23-d1f5-4380-9a3f-1065b4d165a5)

## Step 4: Install Git

``
sudo yum install git -y
``

![NodeAWSGitInstall](https://github.com/user-attachments/assets/f79c8239-5948-4c6c-b4c9-fde5ba968fa8)

## Step 5: Upload Your Node.js App to EC2
**Clone the Project in the Remote VM**

``
git clone https://github.com/SamuelUdeh/nodejs-on-aws-ec2.git
``

![NodeAWSgitclone](https://github.com/user-attachments/assets/557d0bcc-462c-424d-9cac-7976de2d87ba)

## Step 6: Set Up Environment Variables
Create a .env file with the same content as before:


DOMAIN=""

PORT=3000

STATIC_DIR="./client"

PUBLISHABLE_KEY=""

SECRET_KEY=""


## Step 7: Initialize and Start the Project

``
npm install
npm run start
``


![NodeAWSNPMinstallrun](https://github.com/user-attachments/assets/e0b723c8-7a98-4b3f-951f-24a0cdeced56)

## Step 8: Access Your App in Browser

The project is deployed on AWS and can be accessed using the IPv4 Public IP address of your EC2 instance.

[http://<your-ec2-public-ip>:3000](http://<your-ec2-public-ip>:3000)

Replace <your-ec2-public-ip> with the actual public IP address of your EC2 instance.


![NodeAwsOutput](https://github.com/user-attachments/assets/3e43d2d6-82a3-4d6c-a7e5-94c7edace2d3)

# Conclusion
You have successfully deployed a Node.js application on AWS EC2.

# License
This project is licensed under the MIT License. 













