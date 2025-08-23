# Terraform

### Infrastructure as Code (IaC) 


Infrastructure as Code (IaC) is an approach that involves managing and provisioning infrastructure resources using code, just like you would manage software code. 

Instead of manually setting up and configuring infrastructure components, IaC allows you to define your desired infrastructure state using code.

Think of IaC as a recipe or blueprint for your infrastructure. Instead of manually performing actions like creating virtual machines, configuring networks, or setting up databases, you write code that describes these resources and their desired configurations.

When you use IaC, you can treat your infrastructure as a piece of code that can be version-controlled, reviewed, tested, and deployed. 

It brings the benefits of software development practices to infrastructure management, such as collaboration, repeatability, and automation.

### What is Terraform 

Terraform is an open-source infrastructure as code (IaC) tool developed by HashiCorp. 

It enables you to define and provision infrastructure resources in a declarative and version-controlled manner. 

With Terraform, you can describe your desired infrastructure configuration using a simple and human-readable language called HashiCorp Configuration Language (HCL) or JSON.

### Why do we need Terraform 

`Automating the process `: Terraform automates the creation and management of infrastructure resources, reducing manual effort and the risk of errors.

`Enabling Infrastructure as Code `: With Terraform, infrastructure configuration is written as code, allowing for version control, easy collaboration, and reproducibility.

`Supporting Multiple Platforms` : Terraform supports various cloud providers and on-premises infrastructure, providing a unified way to manage different environments.

`Ensuring Consistency` : Terraform ensures consistent infrastructure deployments by applying the same configuration each time, avoiding inconsistencies and configuration drift.

`State Management` : Terraform keeps track of the current infrastructure state, making it easier to manage and update resources without disrupting existing infrastructure.

`Plan and Apply Workflow` : Terraform's plan and apply workflow allows users to preview and validate infrastructure changes before applying them, ensuring control and reducing the chance of unintended consequences.


### Important terminologies of Terraform 

`1.	Providers` : Providers are plugins in Terraform that interact with various infrastructure platforms such as AWS, Azure, or Google Cloud. They handle the API interactions and resource management for the specific platform. Providers are responsible for creating, updating, and deleting resources.

```sh
Example :
provider "aws" {
 region="us-east-1"
}

```

`2.	Resources` : Resources represent the infrastructure components that Terraform manages, such as virtual machines, storage, networks, and databases. Each resource has a specific configuration and attributes.
   
For example, an AWS EC2 instance resource defines the desired characteristics of a virtual machine

```sh
resource "aws_instance"  "myec2" {
ami= "ami-04a0ae173da5807d3"
instance_type= "t2.micro"
}

```

`3.	Variables` : Variables are placeholders for values that can be customized in Terraform configurations. They allow for flexibility and reusability of configurations.

   ```sh
variable "region"{
	description = "AWS region to deploy resources"
	default     = "us-west-2"
}

```

`4.	Modules` : Modules are self-contained, reusable components that encapsulate Terraform configurations. They allow for code organization and reusability by defining a set of resources and variables.

`5.	Outputs` : Outputs in Terraform allow you to retrieve and display information about the provisioned infrastructure after applying the configuration. They can be used for informational purposes or to pass values to other configurations. 


--------------------------------
