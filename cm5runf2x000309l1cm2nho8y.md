---
title: "Introduction to IAM and How to create User , Group , Attach Policy and Role."
datePublished: Sat Jan 11 2025 07:13:09 GMT+0000 (Coordinated Universal Time)
cuid: cm5runf2x000309l1cm2nho8y
slug: introduction-to-iam-and-how-to-create-user-group-attach-policy-and-role
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1736579487794/88b8ddbc-eca1-46ab-ac03-465da7558370.jpeg
tags: aws, learning, devops, linkedin, articles

---

### **🤷‍♂️ What is IAM**

👉AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736573625996/c0bd9e5f-0e62-4c13-a358-299d10bdff1f.png align="center")

### **🤷‍♂️Amazon Resource Name**

👉Amazon Resource Names uniquely identify AWS resources.

👉Every resource in AWS is provided with an ARN.

### 👉ARN Format:

*arn:partition:service:region:account-id:resource*

*arn:partition:service:region:account-id:resourcetype/resource*

*arn:partition:service:region:account-id:resourcetype:resource*

### **👉IAM Hierarchy**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736574054547/04046732-9fe3-40aa-81be-648a7e205460.png align="center")

### **👉IAM Features**

👉Represents an entity that is created in AWS, can be a person or service.

👉No permissions by default. Nothing is allowed.

**👉Access requirement**

👉Programmatic Access: User needs to make API calls from programs or uses CLI to access AWS resources.

👉Management Console Access: User needs to access AWS resources from management console.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736574396578/d9fb47a0-a49b-4fdb-85d6-7720e938fb11.png align="center")

### **🤷‍♂️IAM Policies**

👉Policies are JSON documents which mention what an user or group can do on AWS resources.

👉It defines the Authorization paradigm for AWS resources.

👉Contains 3 components at the least (EAR):

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736575099990/8993ff51-4047-4392-9419-de847ed4f7df.png align="center")

👉Policies can be attached to Users or Groups.

👉Resource based policies: when policies are attached to resources.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736575229404/5ab5d890-8530-4004-b6e1-299ab76f5a29.png align="center")

👉 AWS Managed Policies.

👉Customer Managed Policies.

👉Inline Policies

### **🤷‍♂️IAM Permissions**

👉Permissions are given by attaching policies to users or groups.

👉No permission by default for all IAM users.

👉AWS account “root” credential.

👉Use the policies defined earlier to provide access to users and groups.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736575590476/4b7bb673-9c56-4aaf-a5a3-25b09de1294b.png align="center")

### **🤷‍♂️IAM Roles**

👉Role is similar to an user/group which has permissions/policies attached to it.

👉Roles are temporary access given to anyone who needs to perform the specific task mentioned in the Role.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736576022694/109800f9-c74f-4744-8326-a55e3ed69990.png align="center")

👉Permissions attached to the users are taken away till the time role is getting used.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736576108274/8d409a90-be21-45d9-85c2-2d531972a7f0.png align="center")

### 🤷‍♂️Tasks To Be Performed:

1\. Create 4 IAM users named “Dev1”, “Dev2”, “Test1”, and “Test2”.

2\. Create 2 groups named “Dev Team” and “Ops Team”.

3\. Add Dev1 and Dev2 to the Dev Team.

4\. Add Dev1, Test1 and Test2 to the Ops Team.

### Solution:

1\. Create 4 IAM users named “Dev1”, “Dev2”, “Test1”, and “Test2 ,

Go to IAM Dashboard and click user and create user

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577445489/b98be5e3-b901-40be-9a8d-8ec9996953d3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577483064/4a7651c5-ac29-448d-992e-17ff0139268b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577520264/e8ce92df-c66f-4a84-8509-1334dfcd163b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577579029/de273691-e1f8-4f02-8887-24a94ac5421a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577611579/e03f45f5-86e8-4d33-aea8-e9721a70a8f6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577658071/f3104117-6957-41ce-ac55-6735906fb335.png align="center")

⚡Download the password and all user Dve2, Test1,Test2 create as it is , download the password for login . look at given below I have created all user same as it .

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577722896/23ad9143-f31a-4d88-86bc-9d5d32780f86.png align="center")

. Create 2 groups named “Dev Team” and “Ops Team”

 In IAM dashboard ,go to Group and click create group, and provide group name and , create user group

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577794929/cd2bcdbd-ec4e-45e1-92b0-ff4afab07be1.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577824346/f66bcb3e-7d84-4bd0-b054-1c6475bbef07.png align="center")

  
 ⚡Ops-Team create same as it ,same process we can follow it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577905634/ba2f45f2-fa3f-4e3b-994a-45452dea573b.png align="center")

Add Dev1 and Dev2 to the Dev Team.  Go to User Group and click Dev-Team, into Dev-Team ,click add user and select Dev1,Dev2, and click add users

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577958055/ed75a248-7a7d-4bb4-9017-3807cc8aaaba.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736577999185/3acfbb00-5c6f-4e86-aed8-299b92c2f86d.png align="center")

Add Dev1, Test1 and Test2 to the Ops Team.

Same as it add user in Ops-Team .follow same process

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578061635/82066a5e-b78d-44ec-ab57-65cfa5c2bd65.png align="center")

### 2 Tasks To Be Performed:

1\. Create policy number 1 which lets the users to:

a. Access S3 completely

b. Only create EC2 instances

c. Full access to RDS

2\. Create a policy number 2 which allows the users to:

a. Access CloudWatch and billing completely

b. Can only list EC2 and S3 resources

3\. Attach policy number 1 to the Dev Team from task 1

4\. Attach policy number 2 to Ops Team from task 1

### Solution:

1\. Create policy number 1 which lets the users to:

a. Access S3 completely

b. Only create EC2 instances

c. Full access to RDS 

Go to polices and click create policy and select the service click next select which you give permission and create policy  . First create policy number

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578406609/7340fca2-e693-44a7-8870-160f711933fd.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578447447/f27ea724-e8f9-4201-94f3-581b2b3f85a7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578506006/96db4a73-9c2d-4587-b23e-b6cd44299325.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578541537/e3c2a37f-2f93-4831-845b-df4d86f394b5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578598473/4f567d2b-ffc4-4ccf-922d-263cbb17f15f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578638515/ae2f7df9-9d1c-4046-abb5-187e39914031.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578672824/18022e6b-56dc-457a-85d0-c4a35ce5ad52.png align="center")

👉Create a policy number 2 which allows the users to:

a. Access CloudWatch and billing completely

b. Can only list EC2 and S3 resources  Create same as it is, follow same process above policy-number1 .here I am created policy-number2

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578754540/afc494f3-31fb-423a-8b03-ccc882a508c1.png align="center")

Attach policy number 1 to the Dev Team from task1

 In policy , go to custom policy select your policy and click action , click attach, select group name, Dev-Team and attach policy.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578840453/5579d186-66ee-4d73-a2ce-0efe9ff61374.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578873819/37001907-32e6-4d99-a216-d2e78ba6df8e.png align="center")

⚡Attach policy number 2 to Ops Team from task 1

⚡ Attach policy number 2 to ops-Team same at it follow above process.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736578956707/dec623d3-5eea-4cac-9245-d6b2460ff06e.png align="center")

### 🤷‍♂️3 Tasks To Be Performed:

1\. Create a role which only lets user1 and user2 from task 1 to have complete access to VPCs and DynamoDB.

2\. Login into user1 and shift to the role to test out the feature.

1\. Create a role which only lets user1 and user2 from task 1 to have completeaccess to VPCs and DynamoDB. 

Go to IAM dashboard , click roles , click create role, click custom trust policy, provides ARN of Dev1,Dev2, here user1,user2,.

click next add permission , provides role name and click create role

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736579248016/7175fe5e-d83d-489b-83eb-3632f16d8321.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736579284698/85ae1f65-2497-4c13-8e95-ac23e8735760.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736579332863/6163050a-6eaf-44d6-91a8-7dcd13f37d53.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736579370284/1e85c3d8-9801-4d08-8889-c8360fb83671.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736579404034/6a3f0570-4d71-4275-b46b-2a9bd2d841a7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736579441917/8f474200-1c2b-4982-a884-da821234de0d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736579469910/0506b7b7-4929-4a6f-9388-f448500fea45.png align="center")