---
title: "🤷‍♂️What is VPC and How to Create your own Custom Virtual Private Cloud (VPC) in AWS?"
datePublished: Tue Jan 14 2025 06:47:23 GMT+0000 (Coordinated Universal Time)
cuid: cm5w41ubk000b09kwho3k48o9
slug: what-is-vpc-and-how-to-create-your-own-custom-virtual-private-cloud-vpc-in-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1736837182814/90c07820-fed4-4329-9960-3b3dda24feca.jpeg
tags: aws, technology, learning, cloud-computing, devops, articles, vpc

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736836099447/1d3f0e57-28d8-456a-9b9f-259d8d7b98bd.png align="center")

## **Introduction**

AWS has an extensive infrastructure that spans the entire globe, with multiple regions and availability zones. Now to make this infrastructure accessible to hundreds and thousands of AWS clients, AWS offers a wide range of services. However, the challenge lies in providing each client with their own private space to locate, connect and manage these AWS services which they launched. This challenge is been solved by **Amazon Virtual Private Cloud (AWS VPC).**

**VPC (Virtual Private Cloud)**

AWS VPC lets you provision a logically isolated section of the Amazon Web Services (AWS) cloud where you can launch AWS resources in a virtual network that you define. You have complete control over your virtual networking environment, including a selection of your own IP address ranges, creation of subnets, and configuration of route tables and network gateways (NAT). You can also create a hardware Virtual Private Network (VPN) connection between your corporate data-center and your VPC and leverage the AWS cloud as an extension of your corporate data-center.

VPCs in AWS account are of 2 types -

***Default VPC***

Each AWS account comes with a default VPC that is pre-configured for you, so you can start using it immediately. Default VPC comes with the CIDR block of 16 subnet masks. *For example,* 172.31.0.0/16. It means this VPC can provide up-to 65,536 IP addresses. Although AWS gives you default VPC, which is suitable for creating instances when testing or learning about AWS. It would be best to create a custom VPC to launch your other AWS resources inside that VPC for the production environment.

***Custom VPC***

Custom VPC allows you to customize a virtual network with your desired IP address range. You can create a subnet of both types, which is public subnet & private subnet.

**Subnet**

A subnet is a logical partition of an IP network into multiple, smaller networks. Basically, you are dividing VPC *(large network)* into smaller networks.

You can create two types of subnet inside VPC -

***Public Subnet*** - If a subnet’s traffic is routed to an internet gateway, the subnet is known as a public subnet.

***Private Subnet*** - If a subnet doesn’t have any route to the internet gateway, the subnet is known as a private subnet.

**Internet Gateway**

Internet Gateway is a horizontally scaled, redundant and highly available VPC component that allows your instance to connect to the internet. It allows the user to make the subnet public by providing a route to the internet. With the help of Internet Gateway, an instance can access the internet and the resources outside instance can access the instance.

**Route Table**

A route table contains a set of rules called routes which determine where traffic has to be directed. The route table is also used to add Internet Gateway to the subnet. You can have multiple route tables in a VPC.

You can create two types of route tables inside VPC -

***Public Route Table*** - It is associated with a public subnet that has a route that sends all traffic to the internet gateway.

***Private Route Table*** - It is associated with a private subnet which has no access to the internet.

> ***SOME IMPORTANT POINTS & LIMITATIONS OF AWS VPC AND ITS COMPONENTS***

1. A maximum of ***5 VPCs*** *(soft limit)* can be created ***per region*** in ***one VPC***, with each VPC allowing up-to ***200 subnets***.
    
2. A VPC is ***region-specific*** and cannot extend between regions, while subnets are ***availability zone (AZ) specific***.
    
3. When you create a VPC you must specify an ***IPv4 CIDR*** *(Classless Inter-domain Routing)* block for VPC. The allowed block size is in between ***/16*** *(65,536)* to ***/28*** *(16)* subnet mask.
    
4. When you create a VPC, a default ***Route table, Network Access Control List (NACL)*** and S***ecurity groups*** are automatically created.
    
5. The CIDR block range of a VPC ***cannot be changed*** once it is created, but additional IP ranges can be added.
    
6. Each Amazon account can ***host multiple VPCs*** because VPCs are ***isolated from each other***.
    
7. You can launch instances into your default VPC without needing to know anything about Amazon VPC.
    
8. Default VPCs are assigned a CIDR range of ***172.31.0.0/16***. Default subnets within a default VPC are assigned ***/20 subnet*** masks within the VPC CIDR range.
    
9. You can attach only ***1 Internet Gateway*** to ***1 VPC***.
    
10. You can provide multiple layers of security, including security groups and network access control lists, to help control access to Amazon EC2 instances in each subnet.
    

### **🤷‍♂️How to Create your own Custom Virtual Private Cloud (VPC) in AWS?**

## **Prerequisite**

1. An AWS Account with AWS Console Access
    
2. A valid user with permission for creation and deletion of VPC, EC2 instances.
    

## **Hands-On**

**Step 1 - Creating your VPC**

a) After logging into your AWS Console, under **Services &gt; All Services**, search for “VPC” and click on it to go to the VPC dashboard.

![](https://miro.medium.com/v2/resize:fit:875/1*Ox4Xwa6n_4rKMEhrfpH6Ug.png align="left")

b) On the **VPC** Dashboard, select **Your VPCs** on the left pane of the **VPC** Dashboard.

c) Now click on **Create VPC** to create a VPC.

![](https://miro.medium.com/v2/resize:fit:875/1*oqKAoslyzIQTRGIFWhE1dA.png align="left")

> ***Note:*** *You can also see the* ***Default VPC*** *which is already existing with the* ***CIDR range 172.31.0.0/16***

d) In Resource to create option select **VPC only** *(VPC and more provides a graphical option to create VPC and its resources at single place)*

e) Enter the VPC name which you want to provide *(since I’m using Mumbai Region I will give it as Mumbai-VPC)*

f) Select **IPv4 CIDR manual input** and provide the **IPv4 CIDR** *(I’m giving 10.0.0.0/16)*

g) The rest you can leave it as default and click on **Create VPC**.

> ***Note:*** *Tenancy defines how EC2 instances are distributed across physical hardware and affects pricing.* ***Shared (default)*** *- Multiple AWS accounts may share the same physical hardware.* ***Dedicated Instance (dedicated)*** *- Your instance runs on single-tenant hardware.*

![](https://miro.medium.com/v2/resize:fit:875/1*ASLntczVI22qRtX_GGacug.png align="left")

h) Now you should be able to see the created VPC in the **Your VPCs** dashboard with “Available” status and the CIDR block specified.

![](https://miro.medium.com/v2/resize:fit:875/1*nTAiVtE2euaoaEx45gFxdA.png align="left")

**Step 2 - Creating Subnets**

a) On the **VPC** Dashboard, click **Subnets** on the left pane of the **VPC** Dashboard.

b) Now click on **Create subnet** to create a Subnet.

![](https://miro.medium.com/v2/resize:fit:875/1*IiRk06wqVEFsqsNDpL6ZyQ.png align="left")

c) In **VPC ID** select the VPC which you just created from the drop-down list *(mine was Mumbai-VPC)*. It will automatically take the **VPCs CIRD block**.

d) Provide a name for the Subnet *(I’m giving it as Public-Subnet-1 for my reference)*

e) You can either select the **“Availability Zone (AZ)”** to a specific zone or leave it as **“No preference”** which will automatically assign it any one of the AZ available in the region.

f) The **IPv4 CIRD** in the subnet is the sub-division or smaller part of the VPC CIRD block *(here I’m giving 10.0.0.0/24 which is a total of 256 IPs out of 65,536 IPs which is available in VPC CIDR)*

g) Now click on **Create subnet**.

![](https://miro.medium.com/v2/resize:fit:875/1*YasvjLV3v8go8l4sn_I1ag.png align="left")

h) Now select the created Subnet and click on **Actions** in top left and click on **Edit subnet settings**.

![](https://miro.medium.com/v2/resize:fit:875/1*5PCA7krnzkZMs7obkgytrw.png align="left")

i) In the **Auto-assign IP settings** menu, choose the **check box** to select **Enable auto-assign public IPv4 address** *(this provides a public IP for the instances which are deployed in this subnet)*

j) Click on **Save** to save the changes.

![](https://miro.medium.com/v2/resize:fit:875/1*HYlNqZM1EJtyz-S60XIzhQ.png align="left")

> ***Note:*** *Follow the above same steps* ***“Step 2”*** *complete to create more* ***Public subnets*** *in the VPC (if you want to create* ***Private subnet*** *then follow* ***Step 2 a - g****)*

k) After completing you should have something like this in your account, where you can see the ***Name,*** ***IPv4 CIDR*** of your subnets, the ***no. of IPs available*** to use and the ***AZ*** in which the ***subnet*** is.

![](https://miro.medium.com/v2/resize:fit:875/1*3uikvJ1j-u7oJW7dOgs9RQ.png align="left")

**Step 3 - Creating Internet Gateway**

a) On the **VPC** Dashboard, click **Internet gateways** on the left pane.

b) Now click on **Create internet gateway**.

![](https://miro.medium.com/v2/resize:fit:875/1*3Xccrpkbpo6OcQdO8bWEfw.png align="left")

c) Provide the name for the **Internet gateway** *(Mumbai-IGW)* and click on **Create internet gateway.**

![](https://miro.medium.com/v2/resize:fit:875/1*lVtm337i_5aO54Qs0mrizA.png align="left")

d) Once created you can see the “*successful creation message”* at the top bar but, the **State** option in **Details** menu shows **Detached** *(this is because the Internet gateway has been* ***created but not attached to any VPC****)*

e) To resolve this click on **Actions** and select **Attach to VPC**.

![](https://miro.medium.com/v2/resize:fit:875/1*n4ka9Xe7U4eUfUtM7BIgzw.png align="left")

f) Select the **VPC** from the drop-down or type the name of the VPC and click on it.

g) Now click on **Attach internet gateway** to attach the IGW to the VPC.

![](https://miro.medium.com/v2/resize:fit:875/1*tc-jGIkTNE6PE9vCOgZCbg.png align="left")

h) Once done you now see the **State** option has been changed to **Attached**.

![](https://miro.medium.com/v2/resize:fit:875/1*9S12zSUmi4nemeGyLhWEiA.png align="left")

**Step 4 - Creating Route Tables**

a) On the **VPC** Dashboard, click **Route tables** on the left pane.

b) Now click on **Create route table**.

![](https://miro.medium.com/v2/resize:fit:875/1*hGs8OftzhUxhZU90IjlEqw.png align="left")

c) Provide the **Name** for the Route table *(Public-RT)* and select the **VPC** in which you want to create the route and click on **Create route table**.

![](https://miro.medium.com/v2/resize:fit:875/1*50uxeplUBloRfk8sGNXp9A.png align="left")

d) Now do the same thing for *(Private-RT)* and click on **Create route table**.

![](https://miro.medium.com/v2/resize:fit:875/1*97_ve6LjQRR4c5cZA8PERw.png align="left")

e) Now you should have ***2 route tables*** with you ***1 for Public subnet*** and ***1 for Private subnet*** *(but there are no subnets associated yet)*.

![](https://miro.medium.com/v2/resize:fit:875/1*80WK-iihBpky07OPg3WrMw.png align="left")

f) To attach the subnet to the route table **select the route table** which you want to attach the subnet to and click on **Subnet associations** in the below tab and then click on **Edit subnet associations**.

![](https://miro.medium.com/v2/resize:fit:875/1*M0lrkcWk8U0XN8IirhCMuw.png align="left")

g) Now select the **2 public subnets** and click on **Save associations** to add the subnets to the route table.

![](https://miro.medium.com/v2/resize:fit:875/1*8gkvsC92CbMTuxf_SdnCNQ.png align="left")

h) Now repeat the same steps for **Private-RT** and this time select the **Private subnets** and click on **Save associations**.

![](https://miro.medium.com/v2/resize:fit:875/1*QuffZE-10U8qzu7WDKvYqA.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*2avp7yUA3fCfYdTBk_0vzA.png align="left")

i) After associating the subnets to the respective route tables you should be able to see **2 subnets** association in each of the subnets.

![](https://miro.medium.com/v2/resize:fit:875/1*2OjGCNp97E-ZEOsrK1bGTA.png align="left")