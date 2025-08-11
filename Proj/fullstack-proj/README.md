# aws-fullstack-proj


This is a full-stack AWS deployment project built with Python (Flask) for managing employee data. The application allows users to interact with:

 - MySQL (via Amazon RDS) for storing employee details

 - Amazon DynamoDB for storing employee image metadata

 - Amazon S3 for image storage

 - Hosted on EC2 instances within a custom VPC

 - Uses IAM Role, Security Groups, and Route Tables for secure access and networking

 - Amazon CloudWatch for Monitor CPU, memory, and disk usage for EC2 & Collect logs

 - Optional domain setup via Route 53 and alert notify using SNS


### Tech Stack


| Layer        | Technology                    |
| ------------ | ----------------------------- |
| Backend      | Python (Flask)                |
| Frontend     | HTML (via Flask `templates/`) |
| Database     | Amazon RDS – MySQL            |
| File Storage | Amazon S3                     |
| Metadata DB  | Amazon DynamoDB               |
| Hosting      | Amazon EC2                    |
| IAM/Routing  | IAM Roles, Route Table        |
| Optional DNS | Amazon Route 53               |
| Monitor & logs | Amazon CloudWatch           |
| Alerting      | SNS                          |


----------------------------------------------------------------
