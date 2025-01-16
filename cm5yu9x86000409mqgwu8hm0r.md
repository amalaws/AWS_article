---
title: "🤷‍♂️What is VPC Peering and How to Create Peering Connections Between AWS Virtual Private Clouds (VPCs)"
datePublished: Thu Jan 16 2025 04:37:03 GMT+0000 (Coordinated Universal Time)
cuid: cm5yu9x86000409mqgwu8hm0r
slug: what-is-vpc-peering-and-how-to-create-peering-connections-between-aws-virtual-private-clouds-vpcs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1737002171009/d1754756-d518-4c59-b38b-636a5b014995.jpeg
tags: aws, cloud-computing, devops, articles, vpc, vpc-peering

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737001721903/9ad91b06-6f49-44fa-a320-fd058c50ca4c.png align="center")

**🤔WHAT IS PEERING**

VPC peering is a networking connection between two Virtual Private Clouds (VPCs) that enables communication between instances in different VPCs as if they were within the same network. This allows resources in one VPC to securely communicate with resources in another VPC using private IP addresses.

### Key Concepts:

1. **Private Connectivity**: VPC peering allows private IP addresses in both VPCs to communicate without needing a VPN or the internet.
    
2. **Transitive Peering Not Supported**: Communication can only happen directly between the peered VPCs. A VPC cannot reach a third VPC through a peering connection.
    
3. **VPC Peering Limitations**:
    
    * VPCs must exist within the same region or across regions (in the case of inter-region VPC peering).
        
    * Peering relationships are one-to-one (i.e., only two VPCs can be directly connected via a single peering connection).
        
    * VPC CIDR blocks must not overlap.
        
4. **Routing**: Once peered, you must update the route tables in each VPC to allow traffic to flow between them.
    
5. **Security**: VPC peering does not affect security groups or network ACLs. You must configure security groups and ACLs to allow traffic between instances in peered VPCs.
    

### Use Cases:

* **Cross-Region Communication**: Connecting VPCs in different regions to enable global applications.
    
* **Multiple Accounts**: Peering VPCs across different AWS accounts to allow secure resource sharing.
    
* **Centralized Services**: Connecting multiple VPCs to a central VPC that contains shared resources or services (like DNS or centralized databases).
    

### How to Set Up VPC Peering:

1. **Create a Peering Connection**: Initiate a peering connection request from one VPC to another.
    
2. **Accept the Request**: The owner of the second VPC must accept the peering connection request.
    
3. **Update Route Tables**: Add routes to each VPC's route table to allow traffic to flow between the peered VPCs.
    
4. **Modify Security Groups and NACLs**: Ensure the security settings allow traffic between instances in both VPCs.
    

# **Step 1: Create Peering Connections**

To create a peering connection between VPC A and VPC B:

1. Navigate to the VPC dashboard then scroll down and select “**Peering connections**” from the left-hand side menu.
    
2. Click on the “Create peering connection” button.
    

![](https://miro.medium.com/v2/resize:fit:875/1*C8U7P0roVzUvIYoEVA9bCw.jpeg align="left")

Peering Connections Dashboard

In the “Peering connection settings” section, enter the following information in the available fields:

* **Name — Optional:** VPC A &lt;-&gt; VPC B
    
* **Select a local VPC to peer with &lt;VPC ID Requester&gt;:** Select VPC A from the drop-down list
    
* **Select another VPC to peer with**: Account — My Account, Region — This Region
    
* **VPC ID (Acceptor)**: Select VPC B from the drop-down list
    

Click on the **Create peering connection** button.

![](https://miro.medium.com/v2/resize:fit:875/1*3o4497dTg4-ktIMS_LzdMA.jpeg align="left")

Create a Peering Connection Between VPC A and VPC B

Next, we are taken to a confirmation page indicating that the peering connection between VPC A and VPC B has been requested and is in a **“Pending acceptance”** state. Click on the “Actions” button and click on Accept Request from the drop-down menu in order to complete the peering connection request between the two VPCs.

![](https://miro.medium.com/v2/resize:fit:875/1*f9X_7rP5Q_FqVFNoNxB3PQ.png align="left")

Peering Connection VPC A &lt;-&gt; VPC B request

**To create a peering connection between VPC A and VPC C:**

Repeat the previous steps to create a peering connection between VPC A and VPC C. Enter the following information into the available fields:

* **Name — optional**: VPC A &lt;-&gt; VPC C
    
* **Select a local VPC to peer with &lt;VPC ID (Requestor)&gt;:** Select VPC A from the drop-down list
    
* **Select another VPC to peer with:** Account — My account, Region — This Region
    
* **VPC ID (Acceptor):** Select VPC C from the drop-down list
    

Click on the orange **Create peering connection** button.

![](https://miro.medium.com/v2/resize:fit:875/1*ioaprwsn13pPempdwdkOkA.jpeg align="left")

Create a Peering Connection Between VPC A and VPC C

At the “**Peering connections**” dashboard, select the peering connection between VPC A and VPC C, then click on the Actions button and select “**Accept Request**” from the list of options in the drop-down list.

![](https://miro.medium.com/v2/resize:fit:875/1*kxCIEJOjtrpJsgOyxopSIw.png align="left")

Peering connections dashboard

At this point, we should see that both peering connections have been successfully established between the VPCs for which they’ve been created.

![](https://miro.medium.com/v2/resize:fit:875/1*84i1kAY6wwvQGWsWcr1xlg.jpeg align="left")

# **2\. Update Route Tables**

In the next step, you will update each route table with entries to direct any outbound inter-VPC network traffic to the VPC peering connection (pcx) that has been established with the remote VPC that needs to receive traffic. From the left-hand side menu, select “**Route tables**” to reach the Route tables dashboard.

**Update VPC A Route Table:**

From the dashboard, select the route table named “**VPC A Route Table**” and then click on the **Edit routes** button at the bottom.

![](https://miro.medium.com/v2/resize:fit:875/1*mYE7rTct1BdTuirFuTkiyQ.jpeg align="left")

Edit Route Table of VPC A

On the next screen, click on the “Add route” button to add a new route to the route table that will be used for sending traffic to the VPC B network.

![](https://miro.medium.com/v2/resize:fit:875/1*oYMzinDDavaE8qoJWgZsEg.jpeg align="left")

Add Route to VPC A Route Table

On the next screen, enter the following information in the available fields:

* **Destination**: 10.1.0.0/16
    
* **Target:** Peering Connection
    

![](https://miro.medium.com/v2/resize:fit:875/1*F7sOq1ZcpL1LpUcxK76fNA.jpeg align="left")

Enter Network Address Destination and Target on VPC A Route Table

From the drop-down list, select the peering connection that is labeled as VPC A &lt;-&gt; VPC B

![](https://miro.medium.com/v2/resize:fit:875/1*cbo_1pJ9c1hY8kXaUOZ2SQ.jpeg align="left")

Select Peering Connection for VPC A to VPC B

Next, click on “Add route” again to add a new route that will be used to send traffic to the VPC C network. Enter the following information in the available fields:

* Destination: 10.2.0.0/16
    
* Target: Peering Connection for VPC A &lt;-&gt; VPC C
    

![](https://miro.medium.com/v2/resize:fit:875/1*Z25yE2g5T_-dK9hvKHzQiA.jpeg align="left")

New Route Entry in Route Table

Click on **Save changes**

![](https://miro.medium.com/v2/resize:fit:875/1*14olq_6sqOpZzzNESnuYNw.jpeg align="left")

Updated Route Table for VPC A

**Update the VPC B Route Table:**

From the dashboard, select the route table named “**VPC B Route Table**” and then click on the **Edit routes** button at the bottom.

![](https://miro.medium.com/v2/resize:fit:875/1*CtTRqKNGDzL-c0FyqGBRJA.png align="left")

Update VPC B Route Table

On the next page, click on “**Add route**” button so that we can add a route that will be used for sending traffic to the VPC A network. Enter the following information in the available fields:

* **Destination**: 10.0.0.0/16
    
* **Target**: Peering Connection VPC A &lt;-&gt; VPC B
    

Click on the **Save Changes button**.

![](https://miro.medium.com/v2/resize:fit:875/1*eRXVSI9BwaXo_K_nK3CUxA.jpeg align="left")

Update VPC B Route Table

Next, we see a confirmation that the route table for VPC B has been updated successfully.

![](https://miro.medium.com/v2/resize:fit:875/1*2yQ-J2NFWNvd6Gtxwaob-A.png align="left")

Updated Route Table for VPC B

**Update VPC C Route Table**:

Finally, to update the route table for VPC C, select the **VPC C Route Table** at the dashboard and then click on the “**Edit routes**” button.

![](https://miro.medium.com/v2/resize:fit:875/1*nTkVfz4LIcbcxFnlJq48yA.png align="left")

Edit VPC C Route Table

On the next screen, click on the “Add route” button so that a route can be added for sending traffic to the VPC A network. Enter the following information into the available fields:

* **Destination**: 10.0.0.0/16
    
* **Target**: Peering Connection for VPC A &lt;-&gt; VPC C
    

Click on the **Save changes** button

![](https://miro.medium.com/v2/resize:fit:875/1*h2x0lc2dmz_vEBllidHgJA.jpeg align="left")

Add Route to VPC C Route Table

![](https://miro.medium.com/v2/resize:fit:875/1*0msIDzvqx9nxzCtedLbbqw.jpeg align="left")

Save changes to VPC C Route Table

This completes the updates to the route tables for each of the 3 VPCs that were deployed in this demonstration. In the final step, it is a good idea to test network connectivity between the resources that were deployed in each VPC.

## **Step 3: Test Network Connectivity**

The final step of the VPC Peering exercise is to validate that inter-VPC network connectivity is enabled. This can be accomplished by initiating ICMP ping request from the EC2 instance of a VPC network and sending that request to an EC2 instance or other resource within another VPC.

* **EC2-VPC A IP: 10.0.0.25**
    
* **EC2 VPC B IP: 10.1.0.236**
    
* **EC2 VPC C IP: 10.2.0.173**
    

From the EC2 instance that was deployed in VPC A, I initiated a continuous ping request to the EC2 instance that was deployed in VPC B at IP address 10.1.0.236. This network connectivity was successful as indicated by the ping replies that were received back from the EC2 of VPC B.

I then repeated this test to send ping requests to the EC2 instance that was deployed in the VPC C at IP address 10.2.0.173. This connectivity test was successful as indicated by the ping replies that were received from the EC2 of VPC C and there was 0% packet loss!!!

ICMP ping connectivity testing from the EC2 of VPC A to the EC2s in both VPC B and VPC C were successful! These destination hosts are reachable from my EC2 instance of the VPC A network!!

![](https://miro.medium.com/v2/resize:fit:875/1*wOjVBm0Y2Y_hyGlg_Bd7vA.jpeg align="left")

Next, I initiated an ICMP ping test from the EC2 instance of VPC B to the EC2 instance of VPC C. Look at that! The network connectivity testing fails this time with 100% packet loss!!

**Can you guess why this host in VPC C is unreachable when initiating the request from the EC2 instance of VPC B?**

**Check out my** [**video**](https://youtu.be/LlKjWDGWXdk) **for more details!!**

![](https://miro.medium.com/v2/resize:fit:875/1*wVwGE3-IUm6jdqle59znRQ.jpeg align="left")

ICMP Ping Test from the VPC B network to the VPC C network fails

Thank you for reading!