---
title: "🤷‍♂️What is Cloud Formation and How create of EC2 Instances using CloudFormation and detailed information on Stack Status and Transitions ?"
datePublished: Wed Jan 22 2025 06:23:47 GMT+0000 (Coordinated Universal Time)
cuid: cm67iqb5q000708k3dofi0wvk
slug: what-is-cloud-formation-and-how-create-of-ec2-instances-using-cloudformation-and-detailed-information-on-stack-status-and-transitions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1737526960645/631f7a16-eca2-4014-b2d1-46b390589ad4.jpeg
tags: cloudformation, linux, aws, engineering, learning, devops, learning-journey

---

### **👉AWS**, **CloudFormation** is a service that allows you to define and manage AWS infrastructure as code. With CloudFormation, you can use JSON or YAML templates to describe the resources you want (such as EC2 instances, S3 buckets, VPCs, etc.), and CloudFormation automatically creates and provisions those resources in a repeatable and consistent manner.

### ⚡Key Concepts of AWS CloudFormation:

1. **Templates**: A CloudFormation template is a text file (in JSON or YAML format) that defines the resources and their properties. Templates describe the infrastructure in a declarative manner, meaning you specify **what** resources you want, and CloudFormation takes care of the details of **how** to create them.
    
2. **Stacks**: A stack is a collection of AWS resources that are created and managed together as a single unit. When you create or update a CloudFormation stack, the resources defined in the template are provisioned or modified.
    
3. **Resources**: Resources are the AWS components (like EC2 instances, S3 buckets, Lambda functions, etc.) that are created and managed by CloudFormation. The template defines these resources and their properties.
    
4. **Change Sets**: Change sets allow you to preview changes that will be applied to your stack before actually updating it. This is useful for verifying changes and ensuring that updates will not break the infrastructure.
    
5. **Parameters**: You can define parameters in your CloudFormation template to make it more flexible. These parameters allow you to input values when creating or updating a stack (e.g., the size of an EC2 instance or the name of a bucket).
    
6. **Outputs**: Outputs allow you to return values from your stack, such as the URL of a newly created web app or the IP address of a new EC2 instance.
    
7. **StackSets**: StackSets enable you to create, update, or delete stacks across multiple accounts and regions from a single template.
    

### 👉Advantages of Using CloudFormation:

* ### **Automation**: CloudFormation automates the provisioning and management of your AWS resources, reducing manual intervention.
    
* **Consistency**: Since you are defining your infrastructure as code, CloudFormation ensures that the resources are consistently created in the same way every time.
    
* **Version Control**: The templates can be versioned and stored in a version control system (like Git), allowing you to track changes to your infrastructure over time.
    
* **Reusability**: CloudFormation templates can be reused to create multiple environments (e.g., development, testing, production) with similar infrastructure setups.
    

### 🤔How to Use CloudFormation:

1. **Create a Template**: Write a CloudFormation template in JSON or YAML format that defines the resources you want to create.
    
2. **Deploy a Stack**: Use the AWS Management Console, AWS CLI, or AWS SDKs to create a stack from the template. CloudFormation will automatically create the resources defined in the template.
    
3. **Update or Delete Stacks**: You can update stacks by modifying the CloudFormation template and applying the changes. CloudFormation will determine the necessary actions (e.g., updating resources, creating new ones, or deleting old ones).
    
4. **Monitor**: You can monitor the stack’s creation, update, or deletion process through the CloudFormation console or using CloudFormation events to track progress and errors.
    

### **👉Create of EC2 Instances using CloudFormation.**

**⚡We will be using the below template to create an EC2 Instance**

```yaml
Parameters:
  
  amiId:
    Type: String 
    Default: ami-0df8c184d5f6ae949
    AllowedValues: [ami-0df8c184d5f6ae949, ami-04b4f1a9cf54c11d0]


  Ec2InstanceType:

    Type: String
    Default: t2.micro
    AllowedValues: [t2.micro, t2.small,t1.small,t1.micro,t2.large]

  
  KeyPair:
   
    Type: String
    Default: jan2
    AllowedValues: [jan205, jan2, nov11]


Resources:



  Server1:
    Type: 'AWS::EC2::Instance'
    Properties:
      ImageId: !Ref amiId
      InstanceType: !Ref Ec2InstanceType
      KeyName: !Ref KeyPair


```

Go to the management console, select the CloudFormation stack, and click on Create Stack. Click Next and give the stack name as ec2-stack. Click on Submit.

![](https://miro.medium.com/v2/resize:fit:875/1*eAOizjAdjrjUalm1O23NDg.png align="left")

Stack creation

📌 Once the stack has been created, You can see the EC2 Instance under the resources section below

![](https://miro.medium.com/v2/resize:fit:875/1*vN7Gf2-NIQbgRXh9WbR6vw.png align="left")

Resource

![](https://miro.medium.com/v2/resize:fit:875/1*UA_qM4s6HtLuWaIIk-VwoQ.png align="left")

EC2 Instance

  
**Clean Up Instructions to avoid billing:**

♻️To avoid hourly charges, **remember to delete this stack afterward**, by going to the CloudFormation stack section in the UI and selecting the **Delete** option.

![](https://miro.medium.com/v2/resize:fit:875/1*Npafbbu4u_d5-S1mt7nuwg.png align="left")

Delete Stack

# **🌈 Important to understand stack status and transitions:**

📌Will discuss in detail status transitions for three scenarios: creation, update, and deletion of stacks

For each scenario, we will use the following color code:

➡️ **Gray for intermediate statuses**. You should just wait for the next transition.

➡️**Green for successful end statuses**. Your changes are applied, and everything should be good.

➡️**Blue for successful rollbacked states**, which will require you to review the Events and correct issues before retrying.

➡️**Red for failed states**, which will require you to manually correct issues or, in the worst-case scenario, delete the stack.

## **Create Stack Status Transitions:**

📌 Below flow diagram below will explain in detail about create stack status transitions.

![](https://miro.medium.com/v2/resize:fit:875/1*DwPvlZZihCjdwqKZT3aJwQ.gif align="left")

👉When you trigger stack creation, you will first see the CREATE\_IN\_PROGRESS status.  
👉If the creation process completes without errors, the stack will reach the CREATE\_COMPLETE status.  
👉If there are invalid parameter values, insufficient permissions, or some other initial error, the stack will reach the CREATE\_FAILED status. Inspect the stack Events and correct any issues before retrying.  
👉If there are errors after some resources have been created, the stack will attempt to roll back(ROLLBACK\_IN\_PROGRESS) and remove the new resources.  
\- If the rollback is successful (ROLLBACK\_COMPLETE), you will need to delete the stack before retrying.  
👉If the rollback fails (ROLLBACK\_FAILED), review the stack Events and fix any issues before retrying the rollback process or deleting the stack.

## **🌈 Update Stack Status Transitions:**

📌 Below flow diagram below will explain in detail about update stack status transitions.

![](https://miro.medium.com/v2/resize:fit:875/1*gch-h0_ixtHTg46lrpZCSw.gif align="left")

👉When you trigger a stack update, you will first see the UPDATE\_IN\_PROGRESS status.  
👉If there are errors in the update process, the stack will reach the UPDATE\_FAILED status. You will need to review the stack Events before retrying.  
👉If the desired changes are applied without errors, CloudFormation will perform a cleanup (remove any old resources) and the stack will get to the UPDATE\_COMPLETE\_CLEANUP\_IN\_PROGRESS status.  
👉If cleanup is successful, the stack will get to the UPDATE\_COMPLETE status.  
👉If cleanup fails, it will attempt to roll back the changes (UPDATE\_ROLLBACK\_IN\_PROGRESS).  
👉If rollback fails, the stack will get to the UPDATE\_ROLLBACK\_FAILED status. Review the stack Events and fix any issues before retrying the rollback process or deleting the stack.  
👉If rollback succeeds, it will also trigger a cleanup, and the stack will get to the UPDATE\_ROLLBACK\_COMPLETE\_CLEANUP\_IN\_PROGRESS status.  
👉If the after-rollback cleanup is successful, you will get to the UPDATE\_ROLLBACK\_COMPLETE status. That is, your stack will get to its initial state. You should review the Events before retrying.  
👉If the after-rollback cleanup fails, the stack will get to the UPDATE\_ROLLBACK\_FAILED status. Review the stack Events and fix any issues before retrying the rollback process or deleting the stack.

## **🌈 Delete Stack Status Transitions:**

📌 Below flow diagram below will explain in detail about delete stack status transitions.

![](https://miro.medium.com/v2/resize:fit:875/1*SMmzXPG2HTMmcmgDRUwryA.gif align="left")

👉When you trigger a stack deletion, you will first see the DELETE\_IN\_PROGRESS status.  
👉If the deletion process completes without errors, the stack will reach the DELETE\_COMPLETE status.  
👉If deletion goes wrong, the stack will reach the DELETE\_FAILED status. Inspect the stack Events and correct any issues before retrying.

# **🌈 Summary:**

📌 In the above blog, We discussed in detail about the creation of EC2 Instances using the CloudFormation stack and also discussed the various statuses that a CloudFormation stack can have and the transitions that occur as the stack moves from one status to another.

🕵🏻***I also want to express that your feedback is always welcome. As I strive to provide accurate information and insights, I acknowledge that there’s always room for improvement. If you notice any mistakes or have suggestions for enhancement, I sincerely invite you to share them with me.***

> ***🤩 Thanks for being patient and following me. Keep supporting 🙏***