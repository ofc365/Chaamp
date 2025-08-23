## terraform install
========================

👉 `https://developer.hashicorp.com/terraform/install`

#### 1. ON LINUX


Go to aws and create a Linux-ec2-instance, connect it

```
sudo yum install -y yum-utils shadow-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum -y install terraform
terraform --version
```


#### 2. ON UBUNTU


Go to aws and create an ubuntu-ec2-instance, connect it

```
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
terraform --version
```


#### 3. ON WINDOWS


Open this link and download :- Binary download - `386` and download latest terraform for your windows system

```
https://developer.hashicorp.com/terraform/install#windows
```

Go to c-drive  ---->   program files   --->  create a folder as `terraform` and extract your downloaded `TF` here

( go to your terraform folder and check `terraform exe file` )

open your terminal box or command prompt and run `terraform --version`
