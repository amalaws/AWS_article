---
title: "🤷‍♂️How to Create an Auto Scaling Group of EC2 Instances for High Availability"
datePublished: Sat Jan 18 2025 07:10:18 GMT+0000 (Coordinated Universal Time)
cuid: cm61umpkd000u09kv97cv6uwi
slug: how-to-create-an-auto-scaling-group-of-ec2-instances-for-high-availability
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1737184155811/89224d42-96fb-4fd5-80f0-03180c522492.jpeg
tags: linux, aws, learning, automation, devops, learning-journey

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737183775377/29527edc-5fc2-401c-a641-8ecb7831f706.png align="center")

👉Amazon EC2 Auto Scaling helps you [maintain application availability and lets you automatically add or remove EC2 instances using scaling policies that you define.](https://aws.amazon.com/ec2/autoscaling/)

⚡AWS auto scaling of EC2 instances has many benefits, mainly better fault tolerance, availability and cost management. This lesson will cover configuring many AWS resources, including:

* VPC’s
    
* Launch Templates
    
* security groups
    
* key pairs
    
* Auto Scaling Groups (ASG)
    
* Target Groups
    
* Load Balancers, and more
    

***The steps for this will be to:***

1. Create a VPC with cidr 10.10.0.0/16
    
2. Create three public subnets with 10.10.1.0/24 & 10.10.2.0/24 & 10.10.3.0/24
    
3. Create an autoscaling group using t2.micro instances. All instances should have apache installed on each instance with the ability to check any random IP address and be able to produce a test page. Ensure the autoscaling group is using the public subnets from #2.
    
4. The autoscaling min and max should be 2 and 5.
    
5. Create an Application Load Balancer to distribute traffic to the autoscaling group.
    
6. Create web server security group that allows inbound traffic from HTTP from your Application Load Balancer.
    
7. Create a load balancer security group that allows inbound traffic from HTTP from 0.0.0.0/0.
    

# **👉Create VPC**

Our first step will be to create a VPC. In the AWS dashboard, search for and open *VPC.*

![](https://miro.medium.com/v2/resize:fit:819/1*GQ-VFj99Mp0-OgDl4BjdwA.png align="left")

***On EC2 dashboard, select Create VPC***

![](https://miro.medium.com/v2/resize:fit:756/1*2HFR6ASJ6LPW9U2z9iZRDA.png align="left")

***Select the option for VPC and more. Give the VCP a name and use a CIDR block of 10.0.0.0/16***

![](https://miro.medium.com/v2/resize:fit:613/1*umQRQIKugNKoK6V76yYPng.png align="left")

***Select 3 availability zones. In the dropdown menu, select availability zones us-east-1a, us-east-1b, and us-east-1c.***

![](https://miro.medium.com/v2/resize:fit:618/1*OYVwolZtjfhuphC-PJzgWw.png align="left")

Select 3 public subnets and 0 private subnets. For the 3 public CIDR Blocks, use 10.10.1.0/24, 10.10.2.0/24, and 10.10.3.0/24.

**Keep all other defaults and select Create VPC.**

![](https://miro.medium.com/v2/resize:fit:616/1*gbHwuEslC-OiTRD3HFg2tw.png align="left")

Our VPC has been created successfully. Select *View VPC.* On the VPC dashboard, select actions, then *Edit VPC settings*.

![](https://miro.medium.com/v2/resize:fit:735/1*qYCJWEgYJy8Cr9QwBgfPng.png align="left")

Under *DNS settings* ensure *Enable DNS hostnames* is checked and click *save*.

![](https://miro.medium.com/v2/resize:fit:765/1*zG3B1BTYOpWPcrPUuBUIRg.png align="left")

On the VPC console, select *Subnets*. Select one of our three recently created subnets. Click the *Actions* menu and then *Edit subnet settings*.

![](https://miro.medium.com/v2/resize:fit:823/1*IL-l76CE0MYlVseiTivavQ.png align="left")

Under *Auto-assign IP settings*, ensure *Enable auto-assign public IPv4 addresses* is checked. **Repeat for all three subnets**.

![](https://miro.medium.com/v2/resize:fit:829/1*enS7VLkgIPaW4mchNbT5OQ.png align="left")

# **👉Create A Launch Template**

Next we create a *launch template* that contains the configuration information to launch an EC2 instance. This saves time by storing parameters so that we don't have to specify them every time an instance is created.

In the EC2 dashboard, select *Launch Templates*.

![](https://miro.medium.com/v2/resize:fit:760/1*T2699w1WL2gaIdzTBJfO1A.png align="left")

Select *Create launch template.*

![](https://miro.medium.com/v2/resize:fit:795/1*PZlk6vFJeknHGU8tKq7BhA.png align="left")

Give the template a name and (optional) description.

![](https://miro.medium.com/v2/resize:fit:628/1*oinTZnj6jK5ZdLhmOVscpw.png align="left")

Select *Quick Start* under *Application and OS Images*. Select a *free tier eligible* Amazon Linux AMI. Ensure *Architecture* is set to 64-bit.

![](https://miro.medium.com/v2/resize:fit:758/1*GduDob3qVqdLQnQVDF0EpQ.png align="left")

Under *Instance type* select t2.micro.

![](https://miro.medium.com/v2/resize:fit:613/1*KPKGJlNJhbNBwkGdyg-ZcA.png align="left")

Select a previously created key pair or create a new one for this template. [Amazon documentation on creating new key pairs can be found here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/create-key-pairs.html).

![](https://miro.medium.com/v2/resize:fit:785/1*0qFjQ2MBh_IHmF2Z0cLtkw.png align="left")

Under *Network settings* select *Create security group*. Give the group a name and description. Ensure your recently created VPC is selected from the dropdown menu.

![](https://miro.medium.com/v2/resize:fit:778/1*mNmBLoDHjDSZIco65bUaqQ.png align="left")

*Select Add security group rule*

![](https://miro.medium.com/v2/resize:fit:616/1*mSB_SWenuGmXLpAOzwfQGg.png align="left")

Create a rule allowing *HTTP* from *Anywhere*. This will allow internet traffic to the website. Also allow *SSH* from *My IP*. This will allow you to connect to the instances remotely.

![](https://miro.medium.com/v2/resize:fit:616/1*3kDcsL_y4tzsjQXGtGK-AA.png align="left")

Under *Advanced network configuration* select *Add network interface.*

![](https://miro.medium.com/v2/resize:fit:875/1*wKWQCB9D7IY6gVh6xF8W3A.png align="left")

Select the option to Enable *Auto-assign public IP*.

![](https://miro.medium.com/v2/resize:fit:836/1*BERnbYRRC54E9f16UygsSg.png align="left")

Open *Advanced details* and scroll to the bottom of the menu.

In the *User data* field we will enter data giving instructions to the instance upon creation. This code will install Apache web server as well as notify us of the local IP address of the instance when we visit the website. This will come in handy when testing our load balancer later.

Input the following in the *User data* field.

```plaintext
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
EC2AZ=$(curl -s http://169.254.169.254/latest/meta-data/local-hostname) 
echo '<center><h1>The local IP Address of this Amazon EC2 instance is: AZID </h1></center>' > /var/www/html/index.txt
sed "s/AZID/$EC2AZ/" /var/www/html/index.txt > /var/www/html/index.html
```

Select *Create launch template* and the template will be successfully created.

![](https://miro.medium.com/v2/resize:fit:583/1*14rPi7AeLIFINtbXzDXK7g.png align="left")

![](https://miro.medium.com/v2/resize:fit:614/1*VwYFGGoJCiwhwRa_qDfMUQ.png align="left")

# **👉Create Auto Scaling Group (ASG)**

Next we will create an [auto scaling group](https://docs.aws.amazon.com/autoscaling/ec2/userguide/auto-scaling-groups.html). An auto scaling group contains a collection of EC2 instances that are treated as a logical grouping for the purposes of automatic scaling and management. You can use scaling policies to increase or decrease the number of instances in your group dynamically to meet changing conditions.

On the EC2 dashboard, scroll to the bottom and select *Auto Scaling Groups*.

![](https://miro.medium.com/v2/resize:fit:578/1*srQjCT7pimZQQlI0QOxZVg.png align="left")

Give the group a name and select our previously created launch template from the dropdown menu. Click *Next*.

![](https://miro.medium.com/v2/resize:fit:614/1*bts7RvW8ue3Za-5mZXZQPg.png align="left")

Select our previously created VPC. Under *Availability Zones and Subnets*, select our three public subnets from the dropdown menu. Click *next*.

![](https://miro.medium.com/v2/resize:fit:828/1*9MTOA_EBQeJlKJjG0wyUCQ.png align="left")

Keep the defaults on the *advanced options* page and click next.

![](https://miro.medium.com/v2/resize:fit:834/1*U6pnUPJ9nkqtKeWJePs0kw.png align="left")

On the *Configure group size* menu. select a *desired* and *minimum capacity* of 2. Select a *maximum capacity* of 5.

![](https://miro.medium.com/v2/resize:fit:875/1*6I-DCEoL_vWzwLjXkM9_Hg.png align="left")

Click next on *add notifications.*

![](https://miro.medium.com/v2/resize:fit:838/1*-gAzQE5KzMtFVCYV8kKugA.png align="left")

Click next on *add tags.*

![](https://miro.medium.com/v2/resize:fit:829/1*3axf5O7B6tZ26sT-sgz-Ww.png align="left")

Finally click *Create Auto Scaling Group* on the review page. Auto Scaling group should now be created successfully.

![](https://miro.medium.com/v2/resize:fit:543/1*Ew3PQMgen50VZpxMMPgjZQ.png align="left")

![](https://miro.medium.com/v2/resize:fit:655/1*qZZGL59CxD6XwLPaCqRo5Q.png align="left")

# **👉Create A Target Group**

Now we will create a target group for our load balancer. Target groups route requests to one or more registered targets, such as EC2 instances, using the protocol and port number that you specify.

The load balancer continually monitors the health of all targets registered with the target group and routesrequests to the registered targets that are healthy.

At the bottom of the EC2 dashboard menu, select *Target Group*.

![](https://miro.medium.com/v2/resize:fit:238/1*-4OrqgjX7W-M9dcjNTCtIw.png align="left")

Select *Create target group.*

![](https://miro.medium.com/v2/resize:fit:666/1*XqY2wqmv_eBCu89mI_ivPw.png align="left")

Ensure Instances is selected for *target type*. Give the target group a name.

![](https://miro.medium.com/v2/resize:fit:875/1*bUYK-klHyVb3sPP3Ad9k5Q.png align="left")

Select a *protocol version* of HTTP and *port* 80. Ensure the correct VPC is selected and click next.

![](https://miro.medium.com/v2/resize:fit:675/1*_PMF3PfiayuNaBrdydNLHQ.png align="left")

Leave the rest default and click *Create target group*.

![](https://miro.medium.com/v2/resize:fit:591/1*6r59dLT36e0GxNgmbdTWzw.png align="left")

# **👉Create Load Balancer**

Now we will create our load balancer.

Our load balancer will serve as the single point of contact for clients. It will distribute incoming application traffic across multiple EC2 instances, in multiple Availability Zones increases the availability of our website or application.

On the EC2 dashboard select *Load Balancers.*

![](https://miro.medium.com/v2/resize:fit:219/1*WsK5-sIVpnETKNEumOXoWw.png align="left")

Select *Create load balancer.*

![](https://miro.medium.com/v2/resize:fit:631/1*zNN2uHCGjHbis0OU1BWhrg.png align="left")

Select *Create* under *Application Load Balancer.*

![](https://miro.medium.com/v2/resize:fit:403/1*MjkMxuZV9Rp_Uxy9Q6VKYA.png align="left")

Give the load balancer a name. Select *Internet-facing* schema.

![](https://miro.medium.com/v2/resize:fit:788/1*eCFct_ha03RNXP6RC6bVPg.png align="left")

Under *network mapping*, ensure our VPC is selected, and check the boxes for our public subnets (us-east-1a,1b, and 1c).

![](https://miro.medium.com/v2/resize:fit:781/1*tsdAxbZA_p0H_7UGtCGX2w.png align="left")

Under *Security groups*, remove the default and select our previously created security group which allows http traffic.

![](https://miro.medium.com/v2/resize:fit:454/1*vhlIBUcvFU-leC4Po6dSDg.png align="left")

Under *Listeners and routing*, create a listener using *protocol* http on *port* 80. In the *Forward To* box*,* select our previously created target group.

![](https://miro.medium.com/v2/resize:fit:873/1*seqOHp748rLGdV6QwO3dhQ.png align="left")

Scroll to the bottom and select Create load balancer.

![](https://miro.medium.com/v2/resize:fit:411/1*SUWAhRbG64lCY3cgnUEyPw.png align="left")

Load balancer successfully created.

![](https://miro.medium.com/v2/resize:fit:588/1*3I6l1iHqrl8hUv8zjHurdw.png align="left")

Now we need to ensure any instances created in the future are added to the load balancer. For that we will go to *Auto Scaling Groups* on the EC2 dashboard.

![](https://miro.medium.com/v2/resize:fit:200/1*QHQrGl81WqpcHBRHsZgWHg.png align="left")

Select our Auto Scaling group.

![](https://miro.medium.com/v2/resize:fit:543/1*oVwYDcT4pQ_de-RcPG_ing.png align="left")

Scroll to *load balancing* and click *edit.*

![](https://miro.medium.com/v2/resize:fit:875/1*Awzv5GvZ03wrBLHvRnsXOg.png align="left")

Check the box for *Application, Network, or Gateway Load Balancer target groups*, then select our target group. Click *Update*.

![](https://miro.medium.com/v2/resize:fit:875/1*M5AbKNnulyk-v0VLsuY7Ag.png align="left")

# **👉Verify ASG and Load Balancer Working Properly**

Now, anytime a new instance is launched into the auto scaling group, it will be picked up by the load balancer. With everything completed, lets verify that the autoscaling group and load balancer are working properly.

On the EC2 dashboard, go back to Auto Scaling Groups.

![](https://miro.medium.com/v2/resize:fit:210/1*DQp08ln2xAEaLadgPKYp6w.png align="left")

Select our Group and click on the *instance management* tab.

![](https://miro.medium.com/v2/resize:fit:623/1*yKdlw-RUnRggjFKxvioXZQ.png align="left")

As we configured earlier in the Auto Scaling Group settings, our ASG has automatically created two instances and their status shows healthy.

With ASG verified, lets now check our load balancer. To verify it is functioning, we will go to it’s public dns address from our browser. If working correctly, it will show the webpage for one of our servers. Once we refresh the page, we should see it sent us to a different webpage from a different server showing that the balancer is controlling the traffic.

Select *load balancer* from the EC2 dashboard.

![](https://miro.medium.com/v2/resize:fit:243/1*70icZ88OrcmgFAVjULLGnQ.png align="left")

Select our load balancer.

![](https://miro.medium.com/v2/resize:fit:786/1*Td6WGpheLu2G9x3sRzZEGA.png align="left")

Copy the *DNS name.*

![](https://miro.medium.com/v2/resize:fit:875/1*-ILmz0_vqfydrRsMYYTi9A.png align="left")

Visit the site in your browser, ensure you are using http and not https.

![](https://miro.medium.com/v2/resize:fit:568/1*49DyuhEvKDzx8dOtTCFAeg.png align="left")

When configuring our launch template, our script was set to show the local IP address of the EC2 instance created. Take note of the address on the page.

![](https://miro.medium.com/v2/resize:fit:786/1*YeShTS22ZH9n5rU_YWIDtQ.png align="left")

Refresh the page a few times, the load balancer will distribute the load and take you to a different EC2 instance.

![](https://miro.medium.com/v2/resize:fit:809/1*FIguN2dhrf3Y9h-TSef_dw.png align="left")

Success! Our load balancer is distributing traffic to our multiple instances!