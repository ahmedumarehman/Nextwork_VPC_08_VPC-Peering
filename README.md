<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Peering

**Project Link:** [View Project](https://nextwork.ai/projects/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16)

**Author:** Ahmed Umar Rehman  
**Email:** ahmedumar475@gmail.com

---

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_88727bef)

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a logically isolated virtual network in AWS, and it is useful because it lets you securely control your resources and network traffic.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create two VPCs and establish private communication between them using VPC Peering.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how many networking components must be configured correctly for two VPCs to communicate through VPC Peering.

### This project took me...

This project took me 1.5 hours

## In the first part of my project...

### Step 1 - Set up my VPC

In this step, I will create two VPCs from scratch using the visual VPC resource map because it makes it faster and easier to set up and visualize the required VPC resources.

### Step 2 - Create a Peering Connection

In this step, I will set up a connection link between the two VPCs because VPC Peering allows resources in both VPCs to communicate privately.


### Step 3 - Update Route Tables

In this step, I will set up routes in both VPCs because traffic needs a route in each direction to communicate through the VPC peering connection.

### Step 4 - Launch EC2 Instances

In this step, I will launch an EC2 instance in each VPC because I need resources in both VPCs to test the VPC peering connection.

## Multi-VPC Architecture

I started my project by launching VPC first and then i create 1 public subnet and 0 private subnet

The CIDR blocks for VPCs 1 and 2 are 10.0.0.0/16 and 10.1.0.0/16. They have to be unique because overlapping CIDR ranges can prevent proper communication through VPC Peering


### I also launched 2 EC2 instances

I didn't set up key pairs for these EC2 instances as EC2 Instance Connect manages the key pair for me.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_11111111)

## VPC Peering

A VPC peering connection is a private network connection that allows two VPCs to communicate with each other.

VPCs would use peering connections to enable private communication between resources in different VPCs.

The difference between a Requester and an Accepter is that the Requester initiates the VPC peering connection, while the Accepter accepts the connection request.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_1cbb1b88)

## Updating route tables

After accepting a peering connection, my VPCs' route tables need to be updated because traffic needs a route to reach resources in the other VPC through the peering connection.

My VPCs' new routes have a destination of 10.1.0.0/16 and 10.2.0.0/16. The routes' target was the VPC peering connection.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_4a9e8014)

## In the second part of my project...

### Step 5 - Use EC2 Instance Connect

In this step, I will use EC2 Instance Connect to connect to my first EC2 instance because it provides a way to access the instance directly through the AWS Management Console.

### Step 6 - Connect to EC2 Instance 1

In this step, I will use EC2 Instance Connect to connect to Instance 1 one more time because I need to verify that the public IP and security group changes fixed the connection issue.

### Step 7 - Test VPC Peering

In this step, I will get Instance 1 to send test messages to Instance 2 because I want to test whether the VPC peering connection allows communication between the two VPCs.

## Troubleshooting Instance Connect

Next, I used EC2 Instance Connect to connect to my first EC2 instance and test the VPC peering connection.

I was stopped from using EC2 Instance Connect because my EC2 instance did not have a public IPv4 address assigned.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_7685490c)

## Elastic IP addresses

To resolve this error, I set up Elastic IP addresses. Elastic IP addresses are static public IPv4 addresses that can be assigned to an EC2 instance.

Associating an Elastic IP address resolved the error because it gave my EC2 instance a public IPv4 address required for EC2 Instance Connect.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_45663498)

## Troubleshooting ping issues

To test VPC peering, I ran the command ping <Instance 2's private IP address>.

A successful ping test would validate my VPC peering connection because it confirms that Instance 1 can communicate with Instance 2 through the peering connection.

I had to update my second EC2 instance's security group because it was blocking ICMP traffic. I added a new rule that allows ICMP traffic from the first EC2 instance's security group.

![Image](https://nextwork.ai/calm_indigo_beautiful_lizard/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_7a29d352)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16)*
