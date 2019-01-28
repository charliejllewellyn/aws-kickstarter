# Kickstarter VPN Build Guide

## Introduction

This guide will assist you in deploying a VPN connection between a VPC within AWS and an on premise Data Centre. 

## Pre-Reqs

In order to use this template you must already have configured a VPC as per the guide in the VPC build folder.

### VPN Configuration

<details>
<summary><strong>Create Virtual Gateway</strong></summary><p>

If you havent created a VGW please complete this step.  If not please move to the Create Customer Gateway Section.

1. In the VPC Dashboard select Virtual Private Gateways from the left hand menu. Click the **Create Virtual Private Gateway** button
1. Input a name for the Virtual Private Gateway, in this case we will use *ks-vgw-01*.
1. Leave the **ASN** as *Amazon Default ASN*.
1. Click **Create Virtual Private Gateway**.
1. Once created we need to attach the Virtual Private Gateway to our VPC.  Select the checkbox next to your Virtual Private Gateway.  Then select **Actions > Attach to VPC**.
1. Select your VPC from the drop down menu and click **Yes, Attach**.

</details>

<details>
<summary><strong>Create Customer Gateway</strong></summary><p>

1. In the VPC Dashboard select Customer Gateways from the left hand menu. Click the **Create Customer Gateway** button.
1. Input the following values
   
    | Parameter        | Value           |
    |---|---|
    |**Name**| *ks-onprem-cgw*|
    |**Routing** |*Select Dynamic*|
    |**BGP ASN** |*Input on prem AS number or leave as default*|
    |**IP Address** |*Input Public IP Address of your Customer Gateway*|

1. Your Screen should reflect the below, Click the **Save** button. Then click the **Close** button.

   <p align="left">
      <img width="200" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/11-VPN_Build/images/createCGW.png">
    </p>

</details>
<details>

<summary><strong>Create Site to Site VPN Connection</strong></summary><p>

1. In the VPC Dashboard select Site-to-Site VPN Connections from the left hand menu. Click the **Create VPN Connection** button.
1. Input the following values, Leave the remaining as default.
   
    | Parameter        | Value           |
    |---|---|
    |**Name**| *ks-onprem-aws-vpn*|
    |**Virtual Private Gateway** |*Select Your VPG*|
    |**Customer Gateway** |*Select Existing*|
    |**Customer Gateway ID** |*Select Your Customer Gateway*|
    |**Routing Options** |*Select Dynamic*|
    |**Customer Gateway ID** |*Select Your Customer Gateway*|

1. Your Screen should reflect the below, Click the **Create VPN Connection** button. Then click the **Close** button.

   <p align="left">
      <img width="200" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/11-VPN_Build/images/createVPN.png">
    </p>

</details>
<details>
<summary><strong>Update Route Tables</strong></summary><p>

1. In the VPC Dashboard select Route Tables from the left hand menu. 
1. Select your private route table and select **Actions**  --> **Edit route propogation**.
1. Select the check box to allow route propogation, Click **Save**
   <p align="left">
      <img width="200" src="https://github.com/charliejllewellyn/aws-kickstarter/blob/master/Day1/11-VPN_Build/images/rp.png">
    </p>
1. Repeat this step for your public route table.

</details>
<details>
<summary><strong>Configure Customer Gateway </strong></summary><p>

1. In the VPC Dashboard select select Site-to-Site VPN Connections from the left hand menu.
1. Select your VPN Connection and click **Download Configuration**.
1. In the next window select the options as required.  If your Customer Gateway is not present in the list, select the Generic Template.
1. Select the **Download** button.
1. Complete the configuration on your customer gateway as outlined in the downloaded document.
1. Resources within AWS should now be accesible via thier private IP address ranges.  
</details>