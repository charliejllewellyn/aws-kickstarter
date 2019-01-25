# Overview

This guide introduces basic concepts to enable high availabity on AWS.

This guide will walk through the following scenarios.

1. Deploy a pair of web servers
2. Target group creation
3. Load balancer deployment

## Setting up a load balancer

<details>
<summary><strong>Launch EC2 Instances</strong></summary><p>

1. From the left-hand menu select **Instances**.

1. Click **Launch Instance**. 

1. In the left-hand menu click *My AMI's* and **Select** next to the AMI *ks-linux-webserver*.
    <p align="left">
      <img width="400" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/7-HA_Build/my-amis.png">
    </p>

1. Click **Next: Configure Instance Details**.

1. Under **Network** select the VPC created in the previous lab *ks-vpc-01*.

1. Under **Subnet** select *ks-private-a*.

1. Leave all other options as default and select **Review and Launch**.
    <p align="left">
      <img width="400" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/Create_ec2_instance.png">
    </p>

1. Select **Launch**.

1. At the bottom of the page click the **Targets** tab.

1. Check the box **I acknowledge that I have access to the selected private key file (ks-kerpair.pem), and that without this file, I won't be able to log into my instance.**.

1. Select **Launch Instance**.

1. Repeat the process, for a second instance but this time place the instance in **Subnet** *ks-private-b*.

1. Click **View Instances**.
</details>

<details>
<summary><strong>Create a Target Group</strong></summary><p>

1. From the EC2 console, select **Target Group** from left-hand menu.

1. Click **Create Target Group**.

1. Enter the **Target Group Name** of *ks-targetGroup* and select the **VPC** *ks-vpc-01*.
    <p align="left">
      <img width="300" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/targetgroup.png">
    </p>

1. Click **Create**.

1. At the bottom of the page click the **Targets** tab.

1. Click **Edit** and place a check in box the instances deployed in the previous step.
    <p align="left">
      <img width="400" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/5-EC2_Build/images/targets.png">
    </p>

1. Select **Add to registered** and then click **Save**.

</details>

<details>
<summary><strong>Deploy a load balancer</strong></summary><p>

1. In the EC2 console click **Load balancers** from the left-hand menu.

1. Click **Create Load Balancer**.

1. Click **Create** under **Application Load Balancer**.

1. Enter a **Name** of *ks-alb* and select **VPC** *ks-vpc-01*.

1. Place a check in both subnets and select *ks-public-a* and *ks-public-b*.

1. Click **Next: Configure Security Settings** and then **Next: Configure Security Groups**

1. Click **Create a new security group** and enter **Security group name**.

1. Click **Next: Configure Routing**.

1. In **Target group** select *Existing target group* and in **Name** select *ks-targetGroup*.

1. Click **Next: Register Targets** --> **Next: Review** --> **Create**.

1. Click **Close**.

</details>

<details>
<summary><strong>Test the deployment</strong></summary><p>

1. In the pannel at the bottom copy the **DNS Name** and enter into a browser. You should be presented with the private IP from one of the backend nodes.

1. Click refresh a number of times and you should see the private change between the two web servers.o

1. Now go back to the EC2 console and terminate one of the web servers. 

1. If you refresh the web page again you'll notice that only the web server still available is now serving it's web page.

1. Terminate the second instance.

</details>
