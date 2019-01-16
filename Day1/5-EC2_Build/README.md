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
<summary><strong>Detailed Steps</strong></summary><p>

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

## 3. Automating EC2 software configurations

## 4. Setting up snapshots
