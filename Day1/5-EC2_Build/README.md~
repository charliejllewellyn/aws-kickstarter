# Overview

This guide aims to introduce basic EC2 concepts to help you get started with compute on AWS.

This guide will walk through the following scenarios.

1. Keypair generation
1. Demonstrate deploying a windows AMI and validating coinnectivity to the image.
2. Demonstrate deploying a Linux AMI with automated configuration setup a simple web server
3. Creating snapshots

## 1. Generate a Keypair

**Note** If you are using windows 7 or earlier you will need to download and install Putty and Puttygen from [here](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).

<details>
<summary><strong>Detailed Steps</strong></summary><p>

1. From the AWS console search for EC2 in the search box and select the service. 
    <p align="left">
      <img width="400" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/EC2_console.png">
    </p>

1. From the left-hand menu select **Key Pairs**. 
    <p align="left">
      <img width="200" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/Key_Pair_menu.png">
    </p>

1. Click the **Create Key Pair** button and enter a name for the *ks-keypair* for the demo. This will download the private key to your local machine.
    <p align="left">
      <img width="400" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/Create_key_pair.png">
    </p>

**Note** If you are running windows you need to follow [these instructions](https://aws.amazon.com/premiumsupport/knowledge-center/convert-pem-file-into-ppk/) to convert the key to putty.

</details>

## 2. Deploying AMI's

<details>
<summary><strong>Launch EC2 Instance</strong></summary><p>

1. From the left-hand menu select **Instances**.

1. Click **Launch New Instance**. 

1. Click **Select** next to the AMI *Microsoft Windows Server 2019 Base*.

1. Leave **t2.micro** as the instance type and click **Next: Configure Instance Details** in the bottom right.

1. Under **Network** select the VPC created in the previous lab *ks-vpc-01*.

1. Under **Subnet** select *ks-public-a*.

1. Leave all other options as default and select **Review and Launch**.
    <p align="left">
      <img width="400" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/Create_ec2_instance.png">
    </p>

1. Select **Launch**.

1. Under **Select Key Pair** choose **ks-keypair**.

1. Check the box **I acknowledge that I have access to the selected private key file (ks-kerpair.pem), and that without this file, I won't be able to log into my instance.**.

1. Select **Launch Instance**.

1. Click **View Instances**.
</details>

<details>
<summary><strong>Access Instance</strong></summary><p>

1. Click **Connect**.

1. Click **Get Password** and past in the contents of the Key Pair *ks-keypair* and select **Decrpyt Password**.
    <p align="left">
      <img width="300" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/Windows_password.png">
    </p>

1. Open **Microsoft Remote Desktop** locally.

1. Copy the *hostname*, *username* and *password* that are presented in the AWS Console.
    <p align="left">
      <img width="300" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/RDP_info.png">
    </p>

1. Open the RDP session to login to the newly deployed EC2 instance.

</details>

<details>
<summary><strong>Delete Instance</strong></summary><p>

1. In the AWS Console click **Actions** --> **Instance State** --> **Terminate**.
    <p align="left">
      <img width="300" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/Windows_terminate.png">
    </p>

1. Click **Yes Terminate**.

</details>

## 3. Automating EC2 software configurations

<details>
<summary><strong>Launch EC2 Instance</strong></summary><p>

1. From the left-hand menu select **Instances**.

1. Click **Launch New Instance**.

1. Click **Select** next to the AMI *Amazon Linux 2 AMI (HVM), SSD Volume Type*.

1. Leave **t2.micro** as the instance type and click **Next: Configure Instance Details** in the bottom right.

1. Under **Network** select the VPC created in the previous lab *ks-vpc-01*.

1. Under **Subnet** select *ks-public-a*.

1. Scroll down to the bottom and expand the **Advanced Details** section. 

1. Add the code below into the box labelled *(Optional)*.

```
yum install -y httpd
chkconfig httpd on
echo -e 'echo $(curl http://169.254.169.254/latest/meta-data/local-ipv4) > /var/www/html/index.html' >> /etc/rc.local
chmod 755 /etc/rc.local
service httpd start
```

1. Select **Next: Add Storage**.

1. Select **Next: Add Tags**.

1. Select **Next: Configure Security Group**.

1. Click **Add Rule**.

1. Select **HTTP** from the drop down.
    <p align="left">
      <img width="300" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/linux_sg.png">
    </p>

1. Select **Review and Launch**.

1. Select **Launch**.

1. Under **Select Key Pair** choose **ks-keypair**.

1. Check the box **I acknowledge that I have access to the selected private key file (ks-kerpair.pem), and that without this file, I won't be able to log into my instance.**.

1. Select **Launch Instance**.

1. Click **View Instances**.
</details>

## 4. Setting up snapshots
