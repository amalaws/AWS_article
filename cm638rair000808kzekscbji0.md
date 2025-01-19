---
title: "🤷‍♂️What is RDS and How to Connect to RDS from EC2 ?"
datePublished: Sun Jan 19 2025 06:33:32 GMT+0000 (Coordinated Universal Time)
cuid: cm638rair000808kzekscbji0
slug: what-is-rds-and-how-to-connect-to-rds-from-ec2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1737268350522/b5a57135-6ee5-4b95-b7b5-327c2f9f1209.jpeg
tags: aws, learning, devops, devops-articles

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1737268140642/c93b6eaa-92e4-439a-a9fd-c8627cfd51d1.png align="center")

### **👉Introduction**

AWS RDS (Relational Database Service) is a managed database service provided by Amazon Web Services (AWS). It allows you to easily set up, operate, and scale relational databases in the cloud without needing to manage the underlying infrastructure.

* ### **Importance in Cloud Computing:**
    
* ### **Simplicity: RDS simplifies database management tasks such as provisioning, patching, backup, and scaling, allowing developers to focus more on application development rather than database administration.**
    

* **Scalability**: It offers scalable database solutions with options to increase compute and storage resources as your application demands grow, ensuring performance without downtime.
    

* **Reliability**: AWS manages critical database tasks such as backups, automatic failover, and recovery, enhancing the reliability and availability of your database deployments.
    

* **Security**: RDS integrates with AWS IAM (Identity and Access Management) for fine-grained access control, along with encryption at rest and in transit, ensuring data security compliance.
    

* **Cost-efficiency**: With pay-as-you-go pricing and options like reserved instances, RDS optimizes costs by matching resources to actual usage, eliminating upfront hardware costs and maintenance overhead.
    
    Creating an RDS (Relational Database Service) instance on AWS involves several straightforward steps through the AWS Management Console. Here’s a step-by-step guide:
    

> ***Prerequisites***

1. Have an AWS account. If you don’t have one, sign u[p here](https://aws.amazon.com/) and enjoy the [ben](https://aws.amazon.com/)efits of the [Free-Tier A](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[ccount](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)
    
2. [View proj](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)e[ct files in my Gi](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[tHub](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) [portfolio](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)
    

> [***Lau***](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)***nc***[***h an EC2 Instanc***](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)***e***

1. [O](https://aws.amazon.com/)n the AWS console, search for EC2 and clic[k on](https://aws.amazon.com/) [it to open the](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) EC2 con[sole](https://aws.amazon.com/)
    

![](https://miro.medium.com/v2/resize:fit:875/1*K0sr6mhyZXnoD0IbsLz5PA.png align="left")

2\. Clic[k on](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) [Launch instance a](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)nd launch [an instance with](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) [the following](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) [conf](https://aws.amazon.com/)igurat[ion:](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)

* [Image: A](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)mazon Linux 2 AMI
    
* i[nstance type: t2.](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)micro
    
* security group[: Al](https://aws.amazon.com/)[low ssh(Port](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) 22) and MySQ[L/Au](https://aws.amazon.com/)rora(Port 3306)
    

> [***Cre***](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[***ate***](https://aws.amazon.com/) [***an RD***](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)***S Instance***

1. [On the AWS Con](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[sole, sear](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[ch for RDS](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)
    

![](https://miro.medium.com/v2/resize:fit:875/1*scpXOlTvTYfIZ5XF2EtMmQ.png align="left")

[2.](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) [C](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[lick](https://aws.amazon.com/) [on **Cre**](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)**ate databas**[**e**](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)

![](https://miro.medium.com/v2/resize:fit:875/1*JGrpVuPWxQOts_J57uqzCQ.png align="left")

[3](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[. Sp](https://aws.amazon.com/)[ecify D](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)B details:

* [Database crea](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)t[ion](https://aws.amazon.com/) metho[d — Standard crea](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[te](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)
    
* [En](https://aws.amazon.com/)[gine](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) options — [MySQL](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)
    
* [Ve](https://aws.amazon.com/)[rsion](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) [](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)— Default
    

![](https://miro.medium.com/v2/resize:fit:654/1*T1N9tsV0hG5X4ERWsnq8yA.png align="left")

* [Templates — F](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[ree tie](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[r](https://aws.amazon.com/)
    
* [DB Instance id](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[entifie](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[r —](https://aws.amazon.com/) [dat](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)abase-inst[ance](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) [(Y](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[ou c](https://aws.amazon.com/)[an set your](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) own pref[e](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[rred](https://aws.amazon.com/) [DB Instance](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) [identi](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[fier)](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)
    
* [Master u](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[sername](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) [— rdsuser (You ca](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[n set your own](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) preferred [Master usern](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[ame)](https://aws.amazon.com/)
    
* Master password — Pa55w0rd (You can set [your own preferre](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)d Master pass[word](https://aws.amazon.com/))
    

![](https://miro.medium.com/v2/resize:fit:634/1*sEbBLZl5kvOe7fFz5xs8_g.png align="left")

* [Instance config](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)uration — db.t2.micro
    
* [Storage type](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) — General Purpose [SSD](https://aws.amazon.com/) (g[p2)](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)
    
* [Allocated](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) storage — 20
    
* [Enab](https://aws.amazon.com/)le s[torage autoscalin](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)g — uncheck
    

![](https://miro.medium.com/v2/resize:fit:673/1*w81pdDU4nvkHc6n9pI6V8Q.png align="left")

* P[ubli](https://aws.amazon.com/)[c access — No](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)
    
* VPC S[ecur](https://aws.amazon.com/)ity Group — Cho[ose](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) [existing](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)
    
* [Exis](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)ting [sec](https://aws.amazon.com/)u[rity groups — rem](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[ove](https://aws.amazon.com/) [the defaul](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)t and add [th](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[e security gro](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[up y](https://aws.amazon.com/)ou u[sed for the EC2 (](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)Al[lows SSH and MYS](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)QL/Au[rora traffic)](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)
    

![](https://miro.medium.com/v2/resize:fit:645/1*8L-8g__SXejHVBXaBVGnIQ.png align="left")

Under Additional config[uration, set up](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) the following:

* Initial datab[ase](https://aws.amazon.com/) name — mydb
    
* DB parameter group — default
    
* [Option](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) [gro](https://aws.amazon.com/)[up —](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) default
    
* Enable autom[ated](https://aws.amazon.com/) [backups — u](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[ncheck](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)
    
* [Log ex](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[port](https://aws.amazon.com/)s — uncheck [all](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)
    
* [Lea](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[ve a](https://aws.amazon.com/)[ll](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) [other se](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)ttings [as default](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)
    

![](https://miro.medium.com/v2/resize:fit:646/1*7Sa4XKFwlUfxjGpq5I3ffg.png align="left")

[S](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[crol](https://aws.amazon.com/)[l to](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) t[he bottom and cli](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[ck](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) [on](https://aws.amazon.com/) [**Create d**](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)**atabase**

![](https://miro.medium.com/v2/resize:fit:669/1*UtoRgssMbkoPg0Vd2cEIKg.png align="left")

> [***Create a conn***](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[***ec***](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)***ti***[***on t***](https://aws.amazon.com/)***o th***[***e Amazon RDS data***](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[***base from t***](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)***he EC2 insta***[***nce***](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)

1. [C](https://aws.amazon.com/)[onnect t](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)o the ec2 instance via s[sh](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)
    

![](https://miro.medium.com/v2/resize:fit:874/1*kmu7PAh8RkgAgmpmy0jPow.png align="left")

[2\. Ch](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[ange to root user](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)

```plaintext
sudo su
```

[3](https://aws.amazon.com/). Download s[ome Linux packag](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)es

```plaintext
sudo amazon-linux-extras install epel -y
```

4\. Install [the MySQL reposi](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)tory package. En[ter **y** wherever as](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[ked.](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)

```plaintext
sudo yum install https://dev.mysql.com/get/mysql80-community-release-el7-5.noarch.rpm
```

5\. Ins[tall the MySQL c](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)ommunity server. Enter **y** wherever asked.

```plaintext
sudo yum install mysql-community-server
```

6\. Verify the [version for MySQ](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)L.

```plaintext
mysql --version
```

If [all installed we](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)[ll,](https://aws.amazon.com/) the command should show the MySQL version in[sta](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[lled](https://aws.amazon.com/)

![](https://miro.medium.com/v2/resize:fit:856/1*3f5uprXyiQzs8l4dTa5vlQ.png align="left")

[7\. Get](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) your rds instance Endpoi[nt. On the](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) [database instanc](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)e console, u[nder](https://aws.amazon.com/) the con[nectivity tab, c](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)opy the Endpoint

![](https://miro.medium.com/v2/resize:fit:875/1*RS4AzlVS_ifbdDcY_U1nzA.png align="left")

8[. Run the followi](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)ng command on the termin[al: mysql -h &lt;my](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)sql-instance[\-dns](https://aws.amazon.com/)\&gt; -u &lt;username&gt; -p

In our case, it will be:

```plaintext
mysql -h database-instance.cfjitlrhaxvx.us-east-1.rds.amazonaws.com -u rdsuser -p
```

Press ent[er then enter the](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) password

![](https://miro.medium.com/v2/resize:fit:875/1*BtZKsWsVKkunY2LubfIGrw.png align="left")

> ***Create a Da***[***tabase, Table an***](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)***d In***[***sert***](https://aws.amazon.com/) ***data for testing***

1. Create a data[base](https://aws.amazon.com/):
    

```plaintext
CREATE DATABASE SchoolDB;
```

![](https://miro.medium.com/v2/resize:fit:476/1*5yRJVv4fCfpZkb7OSwjdzQ.png align="left")

2\. You can [see the c](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[reat](https://aws.amazon.com/)[ed d](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)[a](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)tabase through the foll[owing command:](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)

```plaintext
SHOW databases;
```

![](https://miro.medium.com/v2/resize:fit:464/1*53_agGkDxzg4dVBbBpkJtQ.png align="left")

3\. Switch to the databa[se named](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) [SchoolDB](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)

```plaintext
use SchoolDB;
```

![](https://miro.medium.com/v2/resize:fit:509/1*EGS2PfpSjhcNLtgLJG5y3g.png align="left")

4\. Create a [samp](https://aws.amazon.com/)[le table consis](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)ting of Subjects.

```plaintext
CREATE TABLE IF NOT EXISTS subjects (subject_id INT AUTO_INCREMENT,subject_name VARCHAR(255) NOT NULL,teacher VARCHAR(255),start_date DATE,lesson TEXT,PRIMARY KEY (subject_id)) ENGINE=INNODB;
```

5\. Insert some details into the table:

```plaintext
INSERT INTO subjects(subject_name, teacher) VALUES ('English', 'John Taylor');
INSERT INTO subjects(subject_name, teacher) VALUES ('Science', 'Mary Smith');
INSERT INTO subjects(subject_name, teacher) VALUES ('Maths', 'Ted Miller');
INSERT INTO subjects(subject_name, teacher) VALUES ('Arts', 'Suzan Carpenter');
```

6\. Let’s check the items we added into the table:

```plaintext
select * from subjects;
```

![](https://miro.medium.com/v2/resize:fit:821/1*XeV_hyX-NajrX4MCAx_f0g.png align="left")

Congratulations! By following the steps i[n this guide, you](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all)’ve successf[ully](https://aws.amazon.com/) connect[ed your EC2 and](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS) RDS within Amazon We[b Services. This](https://aws.amazon.com/free/?trk=99f831a2-d162-429a-9a77-a89f6b3bd6cd&sc_channel=ps&ef_id=Cj0KCQjw06-oBhC6ARIsAGuzdw03qBfKD7AA8ejOZPfdI7Pg4XshpRd57Q1p-a8--id9VCM5Cjg78xEaAmJtEALw_wcB%3AG%3As&s_kwcid=AL%214422%213%21645125273267%21e%21%21g%21%21aws+free+tier%2119574556890%21145779847112&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free+Tier+Types=*all&awsf.Free+Tier+Categories=*all) connection acts like a s[uperhighway betw](https://github.com/Kevin-byt/AWS-Projects/tree/main/12weeksworkshop/Databases/EC2_RDS)een your computing power and your data storage, allowing your applications to run more efficiently. Now that you’ve set up this connection, you’re all set to manage your data and apps more smoothly within Amazon’s world. This link is key for seamless data operations and application performance. Keep exploring and using this powerful connection to innovate and create within the Amazon ecosystem. It’s your gateway to building robust and scalable systems, opening doors to endless possibilities within AWS.