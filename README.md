# Jumpbox
## Objective:
Set up a Jumpbox (EC2 instance) into public subnet to access a private EC2 instance located in a private subnet which has no direct access to Internet.

## Architecture
![](https://github.com/Jinn42/Jumpbox/blob/master/Architecture_diagram.png)

## 1:Environment setting
Step 1: Create a VPC with /16 IPv4 CIDR block.

Step 2: Set subnet(public subnet & private subnet) with /24 IPv4 CIDR block within one AZ

Step 3: Create an IGW and link it with VPC

## 2:Set instances
Step 1: NAT_Instance
amzn-ami-vpc-nat community AMI and disable Change Source/Dest. Check (Actions > Networking > Change Source/Dest. Check > Yes, Disable)

Step 2: Jumpbox_Instance
Amazon Linux 2 AMI HVM

Step 3: Final_Instance
Amazon Linux 2 AMI HVM

## 3: Elastic IP adress
relate 2 Elastic IPs and assign each of them to the 2 instances in the public subnet: Jumpbox and NAT instance.

## 4: Routetable
Create 2 Route Tables:
Public Route Table associated to the public subnet:
![](https://github.com/Jinn42/Jumpbox/blob/master/Routetable_publicsub.png)

Private Route Table associated to the private subnet:
![](https://github.com/Jinn42/Jumpbox/blob/master/Routetable_privatesub.png)
## 5: Security Group
Create 3 Security Groups and associate each one to its corresponding instance:

Jumpbox Security Group:
NAT instance Security Group:
Final Instance Security Group:

## 6: Test connection by SSH on terminal 


