## Project - Build AWS Infrastructure with IaC Techniques and launch webpage


#### 1. Provider Setup


`vi main.tf`

```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}
```


#### 2. Login your AWS account


`Open once again :- vi main.tf`

Follow this link to create Access key & Secret access key `https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1#/security_credentials/access-key-wizard`

```
# Configure the AWS Account
provider "aws" {
  region     = "ap-south-1"      # define your region
  access_key = "define your access key"  
  secret_key = "define your secret access key"  
}
```

#### 3. Create VPC


```
resource "aws_vpc" "my_vpc" {
    cidr_block = "10.0.0.0/16"

    tags = {
      Name = "first_vpc"
    }
  }
```


##### 3.1 Create subnet :- public


```
resource "aws_subnet" "my_public_subnet" {
    vpc_id     = aws_vpc.my_vpc.id
    cidr_block = "10.0.1.0/24"

    tags = {
      Name = "public_subnet"
    }
  }
```


##### 3.2 Create subnet :- private


```
resource "aws_subnet" "my_private_subnet" {
    vpc_id     = aws_vpc.my_vpc.id
    cidr_block = "10.0.2.0/24"

    tags = {
      Name = "private_subnet"
    }
  }

```

##### 3.3 Create IGW


```
resource "aws_internet_gateway" "my_igw" {
    vpc_id = aws_vpc.my_vpc.id

    tags = {
      Name = "igw"
    }
  }

```


##### 3.4 Create RT & Set-up


```
resource "aws_route_table" "my_routetable" {
    vpc_id = aws_vpc.my_vpc.id

    route {
      cidr_block = "0.0.0.0/0"
      gateway_id = aws_internet_gateway.my_igw.id
    }

    tags = {
      Name = "routetable"
    }
  }

  resource "aws_route_table_association" "public_subnet_association" {
    subnet_id      = aws_subnet.my_public_subnet.id
    route_table_id = aws_route_table.my_routetable.id
  }

  resource "aws_route_table_association" "private_subnet_association" {
    subnet_id      = aws_subnet.my_private_subnet.id
    route_table_id = aws_route_table.my_routetable.id
  }

```

  

##### 3.5 Create security group , by using this sg , create server


```
resource "aws_security_group" "my_sg" {
    name_prefix = "my_sg"
    vpc_id      = aws_vpc.my_vpc.id

    ingress {
      from_port   = 80
      to_port     = 80
      protocol    = "tcp"
      cidr_blocks = ["0.0.0.0/0"]
    }

    ingress {
      from_port   = 443
      to_port     = 443
      protocol    = "tcp"
      cidr_blocks = ["0.0.0.0/0"]
    }

    ingress {
      from_port   = 22
      to_port     = 22
      protocol    = "tcp"
      cidr_blocks = ["0.0.0.0/0"]
    }

    egress {
      from_port        = 0
      to_port          = 0
      protocol         = "-1"
      cidr_blocks      = ["0.0.0.0/0"]
      ipv6_cidr_blocks = ["::/0"]
    }

  }

  resource "aws_instance" "webserver" {
    ami           = "ami-0327f51db613d7bd2"
    instance_type = "t2.micro"
    key_name      = "linux-key" 
    subnet_id     = aws_subnet.my_public_subnet.id
    security_groups = [aws_security_group.my_sg.id]

    user_data = <<-EOF
                  #!/bin/bash
                  sudo apt update
                  sudo apt install -y apache2
                  sudo systemctl start apache2
                  sudo systemctl enable apache2
                  echo "<html><body><h1>Welcome to kloudskart!</h1></body></html>" > /var/www/html/index.html
                  sudo systemctl restart apache2
                  EOF
    tags = {
      Name = "server"
    }
  }

```

##### 3.6 Create EIP


```
resource "aws_eip" "my_eip" {
    instance = aws_instance.webserver.id
  }

```

.

------------------------------


