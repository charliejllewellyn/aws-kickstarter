# Kickstarter VPC Build Guide

## Introduction

This guide will assist you in deploying the fundamental elements of a basic VPC within AWS.  

1. Virtual Private Cloud (VPC)
2. Subnets (Public & Private)
3. Internet Gateway (IGW)
4. NAT Gateway 
5. Virtual Gateway (VGW)
6. Route Table

### Virtual Private Cloud Deployment

1. Firstly we will delete the default VPC created with your account to avoid any confusion later on.
2. In the AWS console select services and then select VPC
3. Within the VPC Dashboard select your VPC's from the left menu and then select Your VPC's.
![select_vpc](../Day1/3-VPC_Build/images/select_vpc.png)
4. Select the tick box next to the default VPC and select **Actions > Delete VPC**.  On the confirmation screen select **Delete VPC**
5. Click **Create VPC**
6. You will then be presented with the screen below. Enter The details as below:  
(Image two)  
    Name tag: *ks-vpc-01*  
IPv4 CIDR block: *10.0.0.0/16*  
IPv6 CIDR block: No IPv6 CIDR Block  
Tenancy: Default. 
7. Click **Create**.

8. On the confirmation screen click close. 

### Create Subnets

1. In the VPC dashboard select subnets from the left menu.
2. Click the **Create Subnet** Button
3. On the next screen input the values as below:  
Name Tag : *ks-public-a*  
VPC: *Select your vpc from the drop down menu*  
Availbility Zone: *eu-west-2a*  
IPv4 Cidr: *10.0.1.0/24*  

    Your screen should be similar to the image below. 
    (image 3)   
4. Click Create and then close once the creation has completed.  
5. Repeat steps 2 - 4 to create subnets as below:    

    Name Tag : *ks-public-b*    
Availability Zone: *eu-west-2b*  
IPv4 Cidr: *10.0.2.0/24*

    Name Tag : *ks-priavte-a*     
Availability Zone: *eu-west-2a*  
IPv4 Cidr: *10.0.11.0/24*

    Name Tag : *ks-private-b*     
    Availability Zone: *eu-west-2b*  
    IPv4 Cidr:*10.0.12.0/24*
    
6. You should now have two private and two public subnets.  We need to set the public subnets to allocate public IP address automatically.     To do this select the tick box next your first public subnet, then select Actions > Modify auto-assign IP settings and tick the **Auto-assign IPv4** box.
7. Repeat step 6 for the second public subnet.

### Create IGW

1. In the VPC Dashboard select Internet Gateways from the left hand menu. Click the **Create Internet Gateway** button
2. In the name tag field insert *ks-igw-01*.
3. Click Create.
4. Once the creation has completed we need to attach the Internet Gateway to our VPC.  Select the tick box next to your IGW and select Actions > Attach to VPC.
5. Select your vpc from the drop down menu and click **Attach**.

### Create NAT Gateway

1. In the VPC Dashboard select NAT Gateways from the left hand menu. Click the **Create NAT Gateway** button
2. In the subnet field select your second public subnet from the dropdown menu.
3. Click the **Create New EIP** button which will populate the second field.
4. Click **Create a NAT Gateway**
5. Once created, click the pencil icon next to your newly created NAT gateway and add the name *ks-natgw-01*, click the tick icon.

### Create Virtual Gateway 

1. In the VPC Dashboard select Virtual Private Gateways from the left hand menu. Click the **Create Virtual Private Gateway** button
2. Input a name for the Virtual Private Gateway, in this case we will use *ks-vgw-01*.
3. Leave the ASN as **Amazon Default ASN**.
4. Click **Create Virtual Private Gateway**.
5. Once created we need to attach the Virtual Private Gateway to our VPC.  Select the checkbox next to your Virtual Private Gateway.  Then select **Actions > Attach to VPC**.
6. Select your VPC from the drop down menu and click **Yes, Attach**.

### Create Route Tables

We will require two route tables within our VPC.  One for the Private Subnets and one for the Public Subnets.  We will start with the Public route table.

1. In the VPC Dashboard select Route Tables from the left hand menu. Click the **Create Route Table** button.
2. Input the following values
   Name Tag: ks-public-rt
   VPC : Select your VPC from the dropdown menu 
3. Click **Create**
4. Once created we need to associate the Public subnets with the public routing table. To do this select the checkbox next to the public route table.  
5. Select **Actions > Edit Subnet Associations**.
6. Select the check boxes next to your two public subnets and click the **Save** button.
7. Select **Actions > Set Main Route Table**.
8. Repeat steps 2 - 6 to create a private route table. Use the values below, Remember to select your **private subnets** when editing the subnet associations:  
  Name Tag: ks-private-rt  
VPC : Select your VPC from the dropdown menu.






  

