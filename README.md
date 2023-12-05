# Caf-Online-Ordering-System---AWS-Lab
Create a secure VPC for café admins, using a bastion host in a public subnet for remote server management. Include a NAT gateway for internet access to an EC2 instance in a private subnet, ensuring a robust and protected network for the café's web application server.

# Café Online Ordering System - AWS Lab

## Table of Contents
1. [Setting Up the Hosting Environment](#setting-up-the-hosting-environment)
   - 1.1 [Configuring an Amazon EC2 Instance](#configuring-an-amazon-ec2-instance)
   - 1.2 [Configuring AWS Cloud9 for Web Development](#configuring-aws-cloud9-for-web-development)
   - 1.3 [Making the Website Accessible](#making-the-website-accessible)
2. [Installing the Café Web Application](#installing-the-café-web-application)
   - 2.1 [Downloading and Extracting Application Files](#downloading-and-extracting-application-files)
   - 2.2 [Copying Café Files to Web Server](#copying-café-files-to-web-server)
   - 2.3 [Configuring Application Parameters](#configuring-application-parameters)
   - 2.4 [Configuring MySQL Database](#configuring-mysql-database)
   - 2.5 [Updating PHP Timezone Configuration](#updating-php-timezone-configuration)
   - 2.6 [Testing Café Website](#testing-café-website)
3. [Duplicating the Café Website](#duplicating-the-café-website)
   - 3.1 [Creating an AMI and Launching Another EC2 Instance](#creating-an-ami-and-launching-another-ec2-instance)
   - 3.2 [Verifying the New Café Instance](#verifying-the-new-café-instance)
4. [VPC Lab](#vpc-lab)
   - 4.1 [Creating a Public Subnet](#creating-a-public-subnet)
   - 4.2 [Creating a Bastion Host](#creating-a-bastion-host)
   - 4.3 [Allocating an Elastic IP for Bastion Host](#allocating-an-elastic-ip-for-bastion-host)
   - 4.4 [Testing Connection to Bastion Host](#testing-connection-to-bastion-host)
   - 4.5 [Creating a Private Subnet](#creating-a-private-subnet)
   - 4.6 [Creating a NAT Gateway](#creating-a-nat-gateway)
   - 4.7 [Creating EC2 Instance in Private Subnet](#creating-ec2-instance-in-private-subnet)
   - 4.8 [Configuring SSH Client for SSH Passthrough](#configuring-ssh-client-for-ssh-passthrough)
5. [Enhancing the Security Layer](#enhancing-the-security-layer)
   - 5.1 [Creating a Network ACL](#creating-a-network-acl)
   - 5.2 [Testing Network ACL](#testing-network-acl)

---

## 1. Setting Up the Hosting Environment<a name="setting-up-the-hosting-environment"></a>
### 1.1 Configuring an Amazon EC2 Instance<a name="configuring-an-amazon-ec2-instance"></a>
- Checked the status of the web server, database, and PHP.
- Started and set up the web server and database to run automatically.

### 1.2 Configuring AWS Cloud9 for Web Development<a name="configuring-aws-cloud9-for-web-development"></a>
- Created a symlink to the web server's directory.
- Adjusted ownership permissions for web server file editing.
- Created a basic test webpage (index.html) in the html directory.

### 1.3 Making the Website Accessible<a name="making-the-website-accessible"></a>
- Edited inbound Rules in the instance Security Group to allow inbound HTTP traffic on TCP port 80 from anywhere.

## 2. Installing the Café Web Application<a name="installing-the-café-web-application"></a>
### 2.1 Downloading and Extracting Application Files<a name="downloading-and-extracting-application-files"></a>
- Downloaded and extracted web server application files.

### 2.2 Copying Café Files to Web Server<a name="copying-café-files-to-web-server"></a>
- Moved café application files to the web server's document root.

### 2.3 Configuring Application Parameters<a name="configuring-application-parameters"></a>
- Configured application parameters in AWS Systems Manager Parameter Store.

### 2.4 Configuring MySQL Database<a name="configuring-mysql-database"></a>
- Configured MySQL database for the café application.

### 2.5 Updating PHP Timezone Configuration<a name="updating-php-timezone-configuration"></a>
- Updated the PHP configuration to set the timezone to "America/New_York."
- Restarted the web server to apply the timezone configuration.

### 2.6 Testing Café Website<a name="testing-café-website"></a>
- Tested whether the café website is working and can be accessed from the internet.

## 3. Duplicating the Café Website<a name="duplicating-the-café-website"></a>
### 3.1 Creating an AMI and Launching Another EC2 Instance<a name="creating-an-ami-and-launching-another-ec2-instance"></a>
- Created an AMI from the existing EC2 instance.
- Set a static internal hostname and created a new key pair.

### 3.2 Verifying the New Café Instance<a name="verifying-the-new-café-instance"></a>
- Verified that the new ProdCafeServer instance in the Oregon Region is running.
- Tested the café web application's functionality.

## 4. VPC Lab<a name="vpc-lab"></a>
### 4.1 Creating a Public Subnet<a name="creating-a-public-subnet"></a>
- Created a public subnet in the Lab VPC.
- Created an internet gateway and attached it to the Lab VPC.
- Updated the route table for the public subnet.

### 4.2 Creating a Bastion Host<a name="creating-a-bastion-host"></a>
- Created an EC2 instance (Bastion Host) in the Public Subnet.
- Configured security group for the bastion host.

### 4.3 Allocating an Elastic IP for Bastion Host<a name="allocating-an-elastic-ip-for-bastion-host"></a>
- Assigned an Elastic IP address to the bastion host.

### 4.4 Testing Connection to Bastion Host<a name="testing-connection-to-bastion-host"></a>
- Tested the SSH connection to the bastion host.

### 4.5 Creating a Private Subnet<a name="creating-a-private-subnet"></a>
- Created a private subnet in the Lab VPC.

### 4.6 Creating a NAT Gateway<a name="creating-a-nat-gateway"></a>
- Created a NAT gateway in the public subnet.
- Created a new route table for the private subnet.

### 4.7 Creating EC2 Instance in Private Subnet<a name="creating-ec2-instance-in-private-subnet"></a>
- Created an EC2 instance (Private Instance) in the Private Subnet.
- Configured security group for the private instance.

### 4.8 Configuring SSH Client for SSH Passthrough<a name="configuring-ssh-client-for-ssh-passthrough"></a>
