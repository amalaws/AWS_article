---
title: "What is EC2 and How to Launch EC2 Step by Step?"
datePublished: Thu Jan 09 2025 09:38:04 GMT+0000 (Coordinated Universal Time)
cuid: cm5p4y2gz000108l0c7uk8dyv
slug: what-is-ec2-and-how-to-launch-ec2-step-by-step
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1736415154517/c3cb1ec4-1615-4031-a7d6-022981bff1d4.jpeg
tags: aws, learning, cloud-computing, devops

---

EC2 (Amazon Elastic Compute Cloud) is a core component of Amazon Web Services (AWS) that provides scalable and resizable compute capacity in the cloud.  
  
⚡**Here are some key features of EC2:**  
  
👉Scalability: You can easily scale your instances up or down based on demand. AWS offers features like Auto Scaling to automatically add or remove instances as needed.  
  
👉**Variety of Instance Types:**  
  
EC2 provides various instance types optimized for different workloads, such as ⚡compute-optimized,⚡ memory-optimized, ⚡GPU instances, and more.  
Security: EC2 instances can be run within a Virtual Private Cloud (VPC) for network isolation. You can also set up firewalls, security groups, and other measures to secure your instances.  
  
👉**Cost-Effective:** You pay for what you use with EC2. There are various pricing models:  
  
👉***On-demand:*** Pay by the hour or second for computing capacity.  
Reserved: Commit to using EC2 instances for a one- or three-year term in exchange for discounted pricing.  
  
👉***Spot Instances:*** Purchase unused EC2 capacity at a discounted rate, ideal for flexible workloads.  
Integration with AWS Services: EC2 integrates well with other AWS services such as Amazon S3, Amazon RDS, Elastic Load Balancing, etc.,  
  
👉***Amazon Machine Images (AMIs)*:** AMIs are pre-configured templates for EC2 instances, containing the operating system, application server, and applications. You can create custom AMIs for your specific needs.  
  
  
👉**Elastic Block Store (EBS):** EC2 instances can use EBS volumes for persistent storage. EBS volumes are durable, meaning they persist even when an instance is terminated.

### **How to launch EC2 Step by Step !!**

Step 1: Sign In to AWS Management Console

1\. Go to the AWS Management Console.

2\. Sign in using your AWS account credentials.

![](https://media.licdn.com/dms/image/v2/D5612AQH1StZPvSPdvA/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736224296873?e=1741824000&v=beta&t=XPhHvTP_mjypGmwhG0FRB68Bo6Jdz0rPcpXtbuvbMOo align="left")

1\. In the AWS Management Console, find the "Services" dropdown menu at the top of the page.

2\. Under the "Compute" section, click on "EC2" to open the EC2 Dashboard.

![](https://media.licdn.com/dms/image/v2/D5612AQHETEi1cKpEcw/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736224358784?e=1741824000&v=beta&t=sJenZ3i21o5s1DhOY0LXQDOXRn4up28GDYyfXE7e_7Q align="left")

Step 3: Launch an Instance

1\. On the EC2 Dashboard, click on the "Launch Instance" button.

![](https://media.licdn.com/dms/image/v2/D5612AQE3CngVFCfFgQ/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736224455018?e=1741824000&v=beta&t=VrLZkuBLMFZoxpD33WiCKSRpD68yvKD8JoZuMx81M8s align="left")

Step 4: Choose an Amazon Machine Image (AMI)

1\. Select an Amazon Machine Image (AMI), which is a template that contains the operating system and software configurations.

2\. You can choose from the following:

o Quick Start: Preconfigured images provided by AWS, such as Amazon Linux, Ubuntu, Windows Server, etc.

o My AMIs: AMIs that you have created or that have been shared with you.

![](https://media.licdn.com/dms/image/v2/D5612AQG6qoaBNT8DCw/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736224603186?e=1741824000&v=beta&t=Poj1LZpfY3I7GKHAQCrMfvJCBQt1a0JZAwo3I5fbyPU align="left")

Step 5: Choose an Instance Type

1\. Choose an Instance Type based on the desired CPU, memory, and networking capacity.

2\. Popular options include t2.micro (eligible for the free tier), m5.large, etc.

3\. Click on "Next: Configure Instance Details".

![](https://media.licdn.com/dms/image/v2/D5612AQHZ2GD7cz3QeQ/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736225117645?e=1741824000&v=beta&t=1JaRteW4c1AE8BJ1RBSjXvSj2lMe_mgnkuVD8YISBns align="left")

Step 6: Configure Instance Details

1\. Configure the instance as needed. Some key options include: o Number of Instances: Specify how many instances you want to launch.

. o Network: Choose the VPC (Virtual Private Cloud) where the instance will reside. o Subnet: Select the subnet within the VPC.

![](https://media.licdn.com/dms/image/v2/D5612AQGusp0SrgxigQ/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736225292898?e=1741824000&v=beta&t=2Bq5qIa0Z6fTBl0wch8xx95CyZnYHuCOESmSAuhCWQw align="left")

Step 7: Configure Security Group

1\. A Security Group acts as a virtual firewall for your instance to control inbound and outbound traffic.

2\. Create a new security group or select an existing one.

o Rule: Define rules such as allowing SSH (port 22) for Linux instances or RDP (port 3389) for Windows instances.

o Source: Specify the IP range that can access the instance (e.g., 0.0.0.0/0 allows access from any IP).

![](https://media.licdn.com/dms/image/v2/D5612AQFnX724USIpAw/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736225348749?e=1741824000&v=beta&t=imAPpZqDKtPKW17cbSWgyp9SjAADBwuP7zeGo0-DdyY align="left")

Step 8: Add Storage

1\. Configure the storage for your instance. By default, AWS assigns an EBS (Elastic Block Store) volume.

2\. You can adjust the size, type (e.g., General Purpose SSD, Provisioned IOPS SSD), and other settings.

3\. Add additional volumes if needed, then click on "Next: Add Tags".

![](https://media.licdn.com/dms/image/v2/D5612AQEjVbSNOy6PsA/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736225685219?e=1741824000&v=beta&t=vQ2OUf1Go_87K07gR00g6JltYRHJBlhEYfen6Mpc7J0 align="left")

![](https://media.licdn.com/dms/image/v2/D5612AQERXqeKtg3YQA/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736225596646?e=1741824000&v=beta&t=U8hGs6QV3b5n46E-YfQMTKEPRVITBUsEntz6dWsiprg align="left")

Step 10: Review Instance Launch 1. Review all your settings and configurations. 2. If everything looks good, click on "Launch".

![](https://media.licdn.com/dms/image/v2/D5612AQH4Wp2D7OI-5A/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736225777115?e=1741824000&v=beta&t=LFBGitjYSGFTdVb0jXlsSCyPFfHmGPyt1xWRn9_BAFo align="left")

Step 11: View and Connect to Your Instance

1\. Click on "View Instances" to see your instance in the EC2 Dashboard.

2\. Wait for the instance State to show "running" and for the Status Checks to pass

![](https://media.licdn.com/dms/image/v2/D5612AQFpb65rT4iPMw/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736225883718?e=1741824000&v=beta&t=C__GOGcZg594CQ--ZEaiy88Qb2lIKWV27jcvPRQGQAI align="left")

Step 12: Connect to Your Instance

1\. For Linux Instances: o Use the command provided in the "Connect" tab to SSH into your instance.

The command typically looks like: ssh -i /path/to/your-key.pem ec2-user@your-instance-public-dns

![](https://media.licdn.com/dms/image/v2/D5612AQEpyLUWjtOsBA/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736226022504?e=1741824000&v=beta&t=ji5LbQBBkwjaVfK3sLFGOmMfjb1TLxc753S9PXZG2hs align="left")

![](https://media.licdn.com/dms/image/v2/D5612AQE-brg-iQnXgg/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1736226052003?e=1741824000&v=beta&t=ncFcmfgfCd8dIP0w6DJ8jqARxJy4DD3GVrT_7SEE_hM align="left")

Your AWS EC2 instance is now launched and ready to use!