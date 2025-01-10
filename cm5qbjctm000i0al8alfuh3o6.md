---
title: "🤷‍♂️What is EFS and How to Mount an AWS EFS to Multiple EC2 Instances ?"
datePublished: Fri Jan 10 2025 05:30:21 GMT+0000 (Coordinated Universal Time)
cuid: cm5qbjctm000i0al8alfuh3o6
slug: what-is-efs-and-how-to-mount-an-aws-efs-to-multiple-ec2-instances
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1736486853050/626d4a4b-45e1-4523-ae36-12091f697524.png
tags: aws, learning, cloud-computing, devops, aws-certified-solutions-architect-associate

---

## **🤷‍♂️What is EFS?**

*👉Amazon Elastic File System (EFS) is a scalable, cloud-native file storage service offered by AWS. It provides a simple, managed file storage solution for workloads that require file-level access, making it ideal for use cases such as web serving, content management, data sharing, and backup.*

### **👉Key Features:**

1. **Fully Managed**: EFS is fully managed, meaning AWS handles all the backend infrastructure, scaling, and maintenance.
    
2. **Scalable**: It automatically scales to accommodate growing storage needs without manual intervention.
    
3. **Accessible**: EFS supports concurrent access from multiple EC2 instances and on-premises servers, allowing for highly available and redundant storage.
    
4. **Performance Modes**: EFS offers two performance modes:
    
    * **General Purpose**: Suitable for most workloads with low-latency requirements.
        
    * **Max I/O**: Designed for workloads that require high throughput and scale.
        
5. **Storage Classes**:
    
    * **Standard**: Ideal for frequently accessed data.
        
    * **Infrequent Access (IA)**: Cost-effective storage for less frequently accessed data.
        
6. **Durability and Availability**: EFS is designed for 99.99% availability and durability by storing data across multiple availability zones.
    
7. **Security**: Integrates with AWS Identity and Access Management (IAM), VPC, and provides encryption at rest and in transit.
    

### 👉Use Cases:

* **Content Management Systems (CMS)**: Store and serve media and content to users.
    
* **Big Data Analytics**: Share large datasets across instances for processing.
    
* **Application Hosting**: Use EFS for web applications that need shared storage.
    
* **Backup and Recovery**: Store backups with high availability.
    

### 👉Key Benefits:

* **Elasticity**: Automatically scales storage as data grows.
    
* **Cost-Effective**: Pay only for what you use, and use storage classes to optimize costs.
    
* **Integration**: Easy integration with other AWS services like EC2, Lambda, and CloudTrail.
    

## **👉How to Mount an AWS EFS to Multiple EC2 Instances ?**

## **Prerequisites**

* **AWS EC2 Instances:** Multiple Ubuntu instances configured in the same VPC as the EFS.
    
* **EFS Created:** An Elastic File System set up in the AWS Management Console.
    
* **Local Linux Machine:** Used to manage and mount the EFS to EC2 instances.
    

## **Steps to Mount EFS on AWS EC2 Instances**

### **Step 1: Switch to Root User**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736485832792/11e40018-6236-4437-af83-bccf12570840.png align="center")

*  
;)This command switches to the root user to ensure you have the necessary privileges to install packages and modify the filesystem.*

### **Step 2: Navigate to the Root Directory**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736485977355/304bf7f6-03b0-4ceb-9383-e193a2a71cfd.png align="center")

### **Step 3: Create a Directory for Mounting the EFS**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736486065740/b3296691-0b5a-4dbc-9db5-059dd917f584.png align="center")

  
Creates a new directory named `efs` at the root level. This directory will serve as the mount point for your EFS.

### ***Step 4: Install Amazon EFS Utilities***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736486159306/9677336e-81a8-4920-98be-4500b195b282.png align="center")

* *Installs the EFS utilities required to mount and manage EFS volumes.*
    
* `yum` *is the package manager used in Amazon Linux; for Ubuntu, use* `apt`*:*
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736486265900/5fd8356e-07fd-4db5-94e3-4814f8fcf8b2.png align="center")

### **Step 5: Attach the EFS**

#### In the AWS Console:

1. Navigate to the **EFS dashboard**.
    
2. Select your EFS and click the **Attach** button.
    
3. Choose **Mount via DNS** (recommended for flexibility and ease of use).
    

#### **Copy the "Using the NFS Client" Command**

The console provides a command similar to the one below. It mounts the EFS using its DNS endpoint.

### **Step 6: Mount the EFS Using the NFS Client**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736486371676/303a2ebd-4802-467c-9d21-2e81f6dbc798.png align="center")

**  
Command Breakdown:**

* `mount`: Mounts a filesystem.
    
* `-t nfs4`: Specifies the NFS version (NFS v4.1) for compatibility and performance.
    
* `-o`: Specifies mount options:
    
    * `nfsvers=4.1`: Uses NFS version 4.1.
        
    * `rsize=1048576`**,** `wsize=1048576`: Set the read/write buffer sizes to 1 MB for optimal performance.
        
    * `hard`: Ensures retries persist if the server becomes unavailable.
        
    * `timeo=600`: Sets a timeout of 600 deciseconds (60 seconds) for retries.
        
    * `retrans=2`: Limits the number of retries to 2.
        
    * `noresvport`: Disables the use of a reserved port.
        
* [`fs-0f69aa5e27936dc87.efs.ap-northeast-2.amazonaws.com`](http://fs-0f69aa5e27936dc87.efs.ap-northeast-2.amazonaws.com)`:/`: The DNS name of the EFS file system.
    
* `efs`: The local directory where the EFS is mounted.
    

## **Verification**

### **Check the Mounted Filesystem**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736486530579/55dff716-45d3-44d6-bc35-95de4af885dc.png align="center")

* Displays the mounted filesystems, showing the EFS under the `/efs` directory.
    

### **Test Write and Read Operations**

1. Create a test file:
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736486615878/267854a5-cc27-480d-9951-e2e17c2aafbd.png align="center")

1. Read the file:
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736486677768/9aaebf09-d34e-4bb1-b60c-0ef50d01ba61.png align="center")

## **Advantages of Mounting via DNS**

* **Flexibility:** The DNS endpoint adjusts to changes in the EFS configuration.
    
* **High Availability:** Ensures reliable access to the EFS from multiple availability zones.
    
* **Ease of Use:** Simplifies the mounting process without needing static IPs.
    

---

## **Conclusion**

By following these steps, you can efficiently mount an AWS EFS to multiple EC2 instances using the DNS method. The shared storage provided by EFS is perfect for distributed systems and applications requiring synchronized access to files across multiple servers.