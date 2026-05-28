# AWS Secure Infrastructure with Bastion Host

## Project Overview

This project demonstrates building a secure AWS infrastructure using a Bastion Host architecture. A public EC2 instance was used to securely access a private EC2 server inside a private subnet.

NGINX was installed on the private EC2 instance to simulate a secure internal application server.

---

## Services Used

* AWS VPC
* Public Subnet
* Private Subnet
* EC2
* Security Groups
* Internet Gateway
* Route Tables
* NGINX
* SSH

---

## Architecture

Internet → Bastion Host (Public EC2) → Private EC2 → NGINX Server

---

## Steps Performed

### 1. Created Custom VPC

Created a custom VPC with CIDR block:

```text id="jlwmk1"
10.0.0.0/16
```

---

### 2. Created Public and Private Subnets

Public Subnet:

```text id="jlwmc3"
10.0.1.0/24
```

Private Subnet:

```text id="jlwmf5"
10.0.2.0/24
```

---

### 3. Configured Internet Gateway and Route Table

* Created Internet Gateway
* Attached Internet Gateway to VPC
* Added public internet route:

```text id="jlwmj8"
0.0.0.0/0 → Internet Gateway
```

---

### 4. Created Bastion Host EC2

* Launched EC2 instance in public subnet
* Enabled Public IP
* Allowed SSH access

---

### 5. Created Private EC2 Instance

* Launched EC2 instance in private subnet
* Disabled Public IP
* Used private networking for secure access

---

### 6. Configured Security Groups

#### Bastion Host Security Group

* Allowed SSH access from My IP

#### Private EC2 Security Group

* Allowed SSH access only from Bastion Host Security Group

---

### 7. Connected to Bastion Host

```bash id="jlwmd8"
ssh -i key.pem ec2-user@public-ip
```

---

### 8. Connected to Private EC2 via Bastion Host

```bash id="jlwmp4"
ssh ec2-user@private-ip
```

---

### 9. Installed NGINX on Private EC2

```bash id="jlwmt7"
sudo yum update -y
sudo yum install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

### 10. Verified NGINX Status

```bash id="jlwmx1"
systemctl status nginx
```

---

## Screenshots

* VPC Configuration
* Public Subnet
* Private Subnet
* Route Table
* Internet Gateway
* Bastion Host EC2
* Private EC2
* Security Groups
* SSH Connection
* NGINX Installation

---

## Challenges Faced

* SSH connectivity troubleshooting
* Security group configuration issues
* Bastion Host setup understanding
* Private EC2 access troubleshooting

---

## Outcome

Successfully created a secure AWS infrastructure using Bastion Host architecture and securely accessed a private EC2 server from a public EC2 instance. Installed and configured NGINX on the private EC2 server.
## Project Screenshots

### VPC
![VPC](screenshots/vpc.png)

### Bastion Host
![Bastion](screenshots/bastion.png)

### Private EC2
![Private](screenshots/private.png)

### SSH Connection
![SSH](screenshots/ssh.png)

### NGINX
![NGINX](screenshots/nginx.png)
