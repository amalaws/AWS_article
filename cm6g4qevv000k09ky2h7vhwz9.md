---
title: "Deploying a Multi-Tier Website Using 
EC2"
datePublished: Tue Jan 28 2025 07:01:53 GMT+0000 (Coordinated Universal Time)
cuid: cm6g4qevv000k09ky2h7vhwz9
slug: deploying-a-multi-tier-website-using-ec2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1738047650769/43784ff3-49aa-4334-a93e-2c1af158a922.jpeg
tags: aws, projects, learning, cloud-computing, devops, devops-articles

---

### **Description: Amazon Elastic Compute Cloud (Amazon EC2) provides scalable computing capacity in the Amazon Web Services (AWS) cloud. Using Amazon EC2 eliminates your need to invest in hardware up front so you can develop and deploy applications faster. You can use Amazon EC2 to launch as many or as few virtual servers as you need, configure security and networking, and manage storage. Amazon EC2 enables you to scale up or down to handle changes in requirements or spikes in popularity, reducing your need to forecast traffic.**

**Problem Statement: Company ABC wants to move their product to AWS.**

**They have the following things set up right now:**

**1\. MySQL DB**

**2\. Website (PHP) The company wants high availability on this product, therefore wants Auto Scaling to be enabled on this website.**

**Steps To Solve: 1. Launch an EC2 Instance**

**2\. Enable Auto Scaling on these instances (minimum 2)**

**3\. Create an RDS Instance**

**4\. Create Database & Table in RDS instance: a. Database name: intel b. Table name: data c. Database password: intel123**

**5\. Change hostname in website**

**6\. Allow traffic from EC2 to RDS instance**

**7\. Allow all-traffic to EC2 instance**

**Solution 1.Luanch EC2**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046076513/e6befb66-a825-4696-b7a1-d494d6874aca.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046115696/3e46f3a2-e969-4f85-a95b-320f7a5b3aaa.png align="center")

**1.. Install apache2 server ..**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046171795/fc212b19-ce13-4528-a305-1a58d8ad9f5f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046193712/5a6786c2-205b-4c92-b434-74e5a6f090d0.png align="center")

**3 . Remove the default page of apache2 go to /var/www/html**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046250883/c1f90328-2bb6-45b3-868f-b0f039bf7bfe.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046269610/d0bb6399-8093-42c0-abee-4bc56540ad4e.png align="center")

  
**4\. Go to command prompt and take your code .. like in download section , or c drive .**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046395283/401598e9-804e-45fd-8ef3-6720bc2a8205.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046814251/e30de4c0-00b9-4d5c-adce-f4d0ad5be051.png align="center")

**Create a database**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046875544/cf1f17ea-ef03-4100-b370-1f3481b97d1c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046899478/ad44b6f4-bc60-4b35-b86c-c3ff7cbc5234.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046917789/9a397f3d-3c21-4447-b182-8e586b936927.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046936556/4a4a0a86-7cc5-468d-b329-f7fb6b669fbd.png align="center")

⚡his is all command to install to client of mysql , and connect to ec2 and unzip the code and also..

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738046956298/ef0cba00-64e6-4aeb-a9ff-9fe204f95e12.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738047000581/9ea377c9-80aa-4a58-bd75-845c99589ea6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738047076243/16265409-f8ec-4af1-bc28-7f56c3ee8687.png align="center")

**👉Create Autoscaling and Load Balancer**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738047103515/fe3fbd49-d2eb-46fc-ad81-1aa953a4523e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738047122639/a35d0dfd-e27c-49ad-9964-ccb10f6def84.png align="center")

  

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738047154448/01595498-7527-4454-8433-e28b71dd61d0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738047175916/6479df91-255e-49e5-b2d4-ab6b867f8877.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738047194765/05a7e4ce-6995-47d1-b8f6-b7241f561b8d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738047215681/2bcdeecf-6df8-4fa0-9b15-bbccd69c7905.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738047259298/daaad5a6-f7c6-4cd8-b352-19fda2b35a77.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738047323565/b952490c-21c5-443f-9a17-cdc8e8e0b6fe.png align="center")

 **👉**Autoscaling is used to automatically adjust the number of computing resources (like virtual machines or containers) in response to the current demand. It helps ensure that your application or service remains available and responsive while optimizing cost and resource usage.

Your web server is running !! and Happy learning 😊