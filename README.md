# Challenge One

A three-tier architecture is a software architecture pattern where the application is broken down into three logical tiers: the presentation layer, the business logic layer and the data storage layer. This architecture is used in a client-server application such as a web application that has the frontend, the backend and the database. Web servers are present in front end, Secured data like code and data will be present as part of backend and database.

In this challenge, I've used below AWS resources to build a three tier infrastructure.

Network:
1) VPC for creating AWS resources in a private network and managing them in a secure and scalable manner.
2) Internet Gateway to allow communication between EC2 Instances in the VPC and the Internet.
3) Two Public Subnets and Two Private Subnets. EC2 instances within a public subnet have public IPs and can directly access the internet while those in the private subnet does not have public IPs and can only access the internet through a NAT gateway.
4) Two Nat Gateways, one for each public subnets
5) Two Elastic IPs to associate with each NAT gateway
6) One Public Route Table and One private Route Table. The public route table will define which subnets will have direct access to the internet ( ie public subnets) while the private route table will define which subnet goes through the NAT gateway (ie private subnets).


Server Configuration:
1) Load Balancer and it's secuirty group:
        The essence of the load balancer is to distribute load across the EC2 instances serving the application. It is attached to two public Subnets. Created a Target group to work along with Auto Scaling Group.
2) Auto Scaling group and Launch Configuration:
        We can simply create two EC2 instances and directly attach these EC2 instances to our load balancer. The problem with that is that our application will no longer scale to accommodate traffic or shrink when there is no traffic to save cost. With Auto Scaling Group, we can achieve this feat. 
3) Bastion host and bastion security group:
        The bastion host is just an EC2 instance that sits in the public subnet. The best practice is to only allow SSH to this instance from your trusted IP.
4) Web server security group



