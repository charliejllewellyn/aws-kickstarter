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
From the AWS console search for EC2 in the search box and select the service. 

<p align="left">
  <img width="400" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/EC2_console.png">
</p>

From the left-hand menu select **Key Pairs**. 

<p align="left">
  <img width="400" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/Key_Pair_menu.png">
</p>

Click the **Create Key Pair** button and enter a name for the *ks-keypair* for the demo. This will download the private key to your local machine.

<p align="left">
  <img width="400" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/Create_key_pair.png">
</p>

**Note** If you are running windows you need to follow [these instructions](https://aws.amazon.com/premiumsupport/knowledge-center/convert-pem-file-into-ppk/) to convert the key to putty.

</details>

## 2. Deploying AMI's

<details>
<summary><strong>Detailed Steps</strong></summary><p>
</details>

## 3. Automating EC2 software configurations

## 4. Setting up snapshots
