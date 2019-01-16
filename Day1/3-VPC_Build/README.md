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

<details>
<summary><strong>Delete Default VPC</strong></summary><p>

1. In the AWS console select services and then select VPC
1. Within the VPC Dashboard select **Your VPCs** from the left-menu and then select Your VPC's.
    <p align="left">
      <img width="200" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/3-VPC_Build/images/select_vpc.png">
    </p>
      
1. Select the tick box next to the default VPC and select **Actions > Delete VPC**.  On the confirmation screen select **Delete VPC**

</details>

<details>
<summary><strong>Create VPC</strong></summary><p>

1. Click **Create VPC**
1. You will then be presented with the screen below. Enter The details as below:  
    <p align="left">
      <img width="200" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/3-VPC_Build/images/create_vpc.png">
    </p>

    | Parameter        | Value           |
    |---|---|
    |**Name tag**| *ks-vpc-01*  |
    |**IPv4 CIDR block**| *10.0.0.0/16*  |
    |**IPv6 CIDR block**| *No IPv6 CIDR Block*|
    |**Tenancy**| *Default*|

1. Click **Create**.
1. On the confirmation screen click close. 

</details>

<details>
<summary><strong>Create subnets</strong></summary><p>

1. In the VPC dashboard select subnets from the left menu.
1. Click the **Create Subnet** Button
1. On the next screen input the values as below:  

    | Parameter        | Value           |
    |---|---|
    |Name Tag : *ks-public-a*  |
    |**VPC**| *Select your vpc from the drop down menu*  |
    |**Availbility Zone**| *eu-west-2a*  |
    |**IPv4 Cidr**| *10.0.1.0/24*  |

    Your screen should be similar to the image below. 
    <p align="left">
      <img width="200" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/3-VPC_Build/images/create_subnet.png">
    </p>  
    
1. Click Create and then close once the creation has completed.  
1. Repeat steps 2 - 4 to create subnets as below:    

    | Parameter        | Value           |
    |---|---|
    |**Name Tag**| *ks-public-b* | 
    |**Availability Zone**| *eu-west-2b*  |
    |**IPv4 Cidr**| *10.0.2.0/24* |

    | Parameter        | Value           |
    |---|---|
    |**Name Tag** | *ks-priavte-a* |
    |**Availability Zone** | *eu-west-2a* |
    |**IPv4 Cidr** | *10.0.11.0/24* |

    | Parameter        | Value           |
    |---|---|
    |**Name Tag**| *ks-private-b* |
    |**Availability Zone**| *eu-west-2b* |
    |**IPv4 Cidr**|*10.0.12.0/24* |
    
1. You should now have two private and two public subnets.  We need to set the public subnets to allocate public IP address automatically.     To do this select the tick box next your first public subnet, then select Actions > Modify auto-assign IP settings and tick the **Auto-assign IPv4** box.
1. Repeat step 6 for the second public subnet.

</details>

<details>
<summary><strong>Create Internet Gateway (IGW)</strong></summary><p>

1. In the VPC Dashboard select Internet Gateways from the left hand menu. Click the **Create Internet Gateway** button
1. In the name tag field insert *ks-igw-01*.
1. Click Create.
1. Once the creation has completed we need to attach the Internet Gateway to our VPC.  Select the tick box next to your IGW and select Actions > Attach to VPC.
1. Select your vpc from the drop down menu and click **Attach**.

</details>

<details>
<summary><strong>Create Nat Gateway</strong></summary><p>

1. In the VPC Dashboard select NAT Gateways from the left hand menu. Click the **Create NAT Gateway** button
1. In the subnet field select your second public subnet from the dropdown menu.
1. Click the **Create New EIP** button which will populate the second field.
1. Click **Create a NAT Gateway**
1. Once created, click the pencil icon next to your newly created NAT gateway and add the name *ks-natgw-01*, click the tick icon.

</details>

<details>
<summary><strong>Create Virtual Gateway</strong></summary><p>

1. In the VPC Dashboard select Virtual Private Gateways from the left hand menu. Click the **Create Virtual Private Gateway** button
1. Input a name for the Virtual Private Gateway, in this case we will use *ks-vgw-01*.
1. Leave the ASN as **Amazon Default ASN**.
1. Click **Create Virtual Private Gateway**.
1. Once created we need to attach the Virtual Private Gateway to our VPC.  Select the checkbox next to your Virtual Private Gateway.  Then select **Actions > Attach to VPC**.
1. Select your VPC from the drop down menu and click **Yes, Attach**.

</details>

<details>
<summary><strong>Create Route Tables</strong></summary><p>

We will require two route tables within our VPC.  One for the Private Subnets and one for the Public Subnets.  We will start with the Public route table.

1. In the VPC Dashboard select Route Tables from the left hand menu. Click the **Create Route Table** button.
1. Input the following values

    | Parameter        | Value           |
    |---|---|
    |**Name Tag**| *ks-public-rt*|
    |**VPC** |*Select your VPC from the dropdown menu* |

1. Click **Create**
1. Once created we need to associate the Public subnets with the public routing table. To do this select the checkbox next to the public route table.  
1. Select **Actions > Edit Subnet Associations**.
1. Select the check boxes next to your two public subnets and click the **Save** button.
    <p align="left">
      <img width="200" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/3-VPC_Build/images/subnet_assoc.png">
    </p>
1. Select **Actions > Set Main Route Table**.
1. Repeat steps 2 - 6 to create a private route table. Use the values below, Remember to select your **private subnets** when editing the subnet associations:  
  
    | Parameter        | Value           |
    |---|---|
    |**Name Tag**| *ks-private-rt* |
    |**VPC**| *Select your VPC from the dropdown menu* |
