---
title: "👉Use CloudFormation to Create a VPC with Subnets"
datePublished: Thu Jan 23 2025 04:52:47 GMT+0000 (Coordinated Universal Time)
cuid: cm68ux4hc000608l2e1oq5mlf
slug: use-cloudformation-to-create-a-vpc-with-subnets
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1737607897552/f58da1a6-86cf-4125-b831-c72882726a6d.jpeg
tags: linux, aws, learning, cloud-computing, devops, articles

---

👉To understand CloudFormation a bit better, we are going to use it to perform the following exercise:

* Create a VPC with CIDR 10.10.0.0/16
    
* Create three public subnets with CIDRs 10.10.1.0/24, 10.10.2.0/24 & 10.10.3.0/24
    

After logging into your AWS account, search for “CloudFormation” and open it up. On the CloudFormation dashboard, click “Create stack.”

![](https://miro.medium.com/v2/resize:fit:875/1*pE8gqYH37I8vLfgOpW3yxg.png align="left")

You have the option to select a pre-existing template (one you’ve already created), use a sample template, or create a new template using Designer. Remember that a CloudFormation template is simply a JSON or YAML text file. If you haven’t used Designer before, it is probably easiest to simply create your text file to define your template code. You can use any text editor to create your text file, but for this example, I will use VS Code. Let’s navigate away from the CloudFormation console for a moment, and open up a new VS Code file. I will be using YAML to create a template, and we will walk through each step of the code. Here is an example of a YAML-formatted template fragment:

### **👉YAML CODE FOR VPC CREATION**

**Parameters: EnvironmentName: Description: An environment name that is prefixed to resource names Type: String VpcCIDR: Description: Please enter the IP range (CIDR notation) for this VPC Type: String Default: 10.192.0.0/16 PublicSubnet1CIDR: Description: Please enter the IP range (CIDR notation) for the public subnet in the first Availability Zone Type: String Default: 10.192.10.0/24 PublicSubnet2CIDR: Description: Please enter the IP range (CIDR notation) for the public subnet in the second Availability Zone Type: String Default: 10.192.11.0/24 PrivateSubnet1CIDR: Description: Please enter the IP range (CIDR notation) for the private subnet in the first Availability Zone Type: String Default: 10.192.20.0/24 PrivateSubnet2CIDR: Description: Please enter the IP range (CIDR notation) for the private subnet in the second Availability Zone Type: String Default: 10.192.21.0/24 Resources: VPC: Type: AWS::EC2::VPC Properties: CidrBlock: !Ref VpcCIDR EnableDnsSupport: true EnableDnsHostnames: true Tags: - Key: Name Value: !Ref EnvironmentName InternetGateway: Type: AWS::EC2::InternetGateway Properties: Tags: - Key: Name Value: !Ref EnvironmentName InternetGatewayAttachment: Type: AWS::EC2::VPCGatewayAttachment Properties: InternetGatewayId: !Ref InternetGateway VpcId: !Ref VPC PublicSubnet1: Type: AWS::EC2::Subnet Properties: VpcId: !Ref VPC AvailabilityZone: !Select \[ 0, !GetAZs '' \] CidrBlock: !Ref PublicSubnet1CIDR MapPublicIpOnLaunch: true Tags: - Key: Name Value: !Sub ${EnvironmentName} Public Subnet (AZ1) PrivateSubnet1: Type: AWS::EC2::Subnet Properties: VpcId: !Ref VPC AvailabilityZone: !Select \[ 0, !GetAZs '' \] CidrBlock: !Ref PrivateSubnet1CIDR MapPublicIpOnLaunch: false Tags: - Key: Name Value: !Sub ${EnvironmentName} Private Subnet (AZ1) PublicRouteTable: Type: AWS::EC2::RouteTable Properties: VpcId: !Ref VPC Tags: - Key: Name Value: !Sub ${EnvironmentName} Public Routes DefaultPublicRoute: Type: AWS::EC2::Route DependsOn: InternetGatewayAttachment Properties: RouteTableId: !Ref PublicRouteTable DestinationCidrBlock: 0.0.0.0/0 GatewayId: !Ref InternetGateway PublicSubnet1RouteTableAssociation: Type: AWS::EC2::SubnetRouteTableAssociation Properties: RouteTableId: !Ref PublicRouteTable SubnetId: !Ref PublicSubnet1 PrivateRouteTable1: Type: AWS::EC2::RouteTable Properties: VpcId: !Ref VPC Tags: - Key: Name Value: !Sub ${EnvironmentName} Private Routes (AZ1) Outputs: VPC: Description: A reference to the created VPC Value: !Ref VPC PublicSubnets: Description: A list of the public subnets Value: !Join \[ ",", \[ !Ref PublicSubnet1 \]\] PrivateSubnets: Description: A list of the private subnets Value: !Join \[ ",", \[ !Ref PrivateSubnet1\]\] PublicSubnet1: Description: A reference to the public subnet in the 1st Availability Zone Value: !Ref PublicSubnet1 PrivateSubnet1: Description: A reference to the private subnet in the 1st Availability Zone Value: !Ref PrivateSubnet1**

Now that our template file is ready to go, let’s navigate back to the CloudFormation console. We previously had clicked the “Create stack” button, so you should see the screen below.

![](https://miro.medium.com/v2/resize:fit:875/1*bVzxfF-vTLdu0dTa_E3fkw.png align="left")

Select “Template is ready” and “Upload a template file.” Click on “Choose file” and select the YAML or JSON template you created in VS Code or some other text editor. After you see that the file is attached, click “Next.”

We are now asked to specify stack details. Give the stack a name and the environment a name. You should see the public subnets you created from your template code, with associated CIDR blocks. On this screen, you are able to edit the subnet and VPC CIDR blocks if desired. Mine look correct, so I will just click “Next.”

![](https://miro.medium.com/v2/resize:fit:875/1*eqdo0ajRBCfCgL24YYyiuw.png align="left")

We now have more configuration options. You can enter a key tag if desired, and assign permissions. For this example, I will leave Tags and Permissions blank. By not assigning an IAM role name, the stack will be created using the credentials of the user that is currently logged in and creating the stack (in this case, myself).

![](https://miro.medium.com/v2/resize:fit:875/1*MsTAHduOvYdKtL5Q9Ewndw.png align="left")

Select “Roll back all stack resources” to ensure that if there is a failure, CloudFormation reverts back to the last known stable state.

![](https://miro.medium.com/v2/resize:fit:875/1*SakQajJxxfTYF-00JSVzTA.png align="left")

Feel free to explore the “Advanced options,” but for the purposes of this tutorial, we will simply click “Next.”

![](https://miro.medium.com/v2/resize:fit:875/1*tEZbJhUNbPuv6JIeiid9LA.png align="left")

Review your settings and when satisfied, click “Submit.” You will see that the creation of your stack is in progress.

![](https://miro.medium.com/v2/resize:fit:875/1*IsqzMHHcm7_rie5dLU97cg.png align="left")

As the stack is created, you will see a log of all the events taking place. Some will take longer to complete than others. Here’s an example, and you can see the creation of the stack, default public route, internet gateway attachment, etc.

![](https://miro.medium.com/v2/resize:fit:875/1*3clHjFGwYdl2pGkFY190iw.png align="left")

We can confirm that our VPC was created by navigating the the VPC console. You can see in addition to the Default VPC, the new W7environment VPC that was specified earlier under the “Parameters” setting has been created.

![](https://miro.medium.com/v2/resize:fit:875/1*6MUPnmhl1J2TRiAC39cMXg.png align="left")

You can navigate to Subnets, Route Tables, Internet Gateways, to see all of the ones that were created with the YAML template file.

![](https://miro.medium.com/v2/resize:fit:875/1*QcoOy20RHkG7IHzna_Lv6Q.png align="left")

Three subnets created

![](https://miro.medium.com/v2/resize:fit:875/1*Bb6nT6K6YRRGCb1D4V8Jxg.png align="left")

Route table created with subnets associated

![](https://miro.medium.com/v2/resize:fit:875/1*83wtFhyY_hjCMLPS8sT34Q.png align="left")

Internet gateway created with VPC associated

Congratulations on creating a CloudFormation template! Templates can be honed and crafted to improve deployment speed, offer consistency amongst applications, and increase security by decreasing human error. In my next tutorial, I will show you how to add auto scaling and a load balancer to a template, all through the CloudFormation console. Stay tuned!