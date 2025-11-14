# aws-HighlyAvailable-WebApp
A highly Available Web Application architecture built using VPC, ALB, ASG, S3

This project deploys a Highly Available Web Application on AWS.
Resources Used:

VPC :  A Virtual Private Cloud(VPC) is created with a private & public subnet across 2 Availability Zones	

NAT Gateways : NAT GWs provides outbound Internet access for instances in private subnets

IAM Role and SSM : An EC2 IAM Role gives necessary permissions(policies) to securely access AWS Services (such as S3, SSM)
Systems Manager Session Manager is used to access the instance without SSH or Keypairs
Gateway Endpoint-S3 : Allows for private access to S3 without going through Internet

Auto Scaling Group (ASG) : Automatically  Scales up or down based on traffic volumes. Helps for high availability and scalability by automatically launching EC2 instances

Application Load Balancer (ALB) : An internet facing ALB distributes incoming traffic to available EC2 instances

Security Groups : Security Groups are used to control inbound/outbound traffic

Summary of Data Flow:
1.	Users access the application via the ALB DNS name
2.	The ALB checks the listener and forwards traffic to target group
3.	Target group forwards traffic to EC2 instance inside private subnets containing the Web Application
4.	If needed, The Web Application uses S3 Gateway endpoint to fetch resources available in S3 bucket 
