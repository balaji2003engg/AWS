# AWS-VPC
Problem statement: Create the EC2 machine in public subnet and another EC2 machine with private subnet with NAT gateway

1. Create the VPC and name it as CGTraining


VPC --- 10.0.0.0/26-------> 32-26 =6 --- > 2 ^6 ==64

2. Create the   below subnets with below CDIR blocks


PublicSubnet1 10.0.0.0/28------->32-28 =4 -----> 2^4 = 16


publicsubnet2 10.0.0.16/28 ------




privatesubnet1 10.0.0.32/28




privatesubnet2   10.0.0.48/28


3. Create the IGW and  attach to the VPC


4.Create the Route  tables
    i) create the public route table . Attach the publicsubnet1 , privatesubnet2 and IGW
   ii) Create the private route table.Attach the privatesubnet1 and privatesubnet2


5. Create the  ec2 machine (name it as public)with public subnet and another  EC2 machine(name it as private) with private subnet. Access the private subnet EC2 machine from the public subnet EC2 machine.Private Ec2 machine does not have the internet access


6. Create the NAT gateway  and attach to the private route table. Now you were able to access internet of the private subnet EC2 machine.
