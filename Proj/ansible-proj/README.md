## Ansible-proj


### Create Ubuntu-ec2 and install Ansible

```
sudo apt-add-repository ppa:ansible/ansible

sudo apt update

sudo apt install ansible -y

ansible --version
```

### Create 2-EC2 instances & Declare as Worker system

### Go to Ansible-system update inside inventory

```
sudo vi /etc/ansible/hosts
```

Update:

```
[workers]
worker_1 ansible_ssh_host=worker-sys pub ip
worker_2 ansible_ssh_host=worker-sys pub ip
```

### create a directory for storing key inside

```
mkdir keys
cd keys/
```

`scp -i "mykey.pem" mykey.pem ubuntu@<ansible-system-pub-dns>:/home/ubuntu/keys`


### Go to Ansible-system , update inside inventory

```
sudo vi /etc/ansible/hosts
```

Update:

```
[workers:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/keys/mykey.pem
```


### Test 


```
sudo ansible workers -m ping
```

```
ansible-inventory --list
```


### Create index.html and Playbook file

```
vi index.html
```

```
vi myansible_playbook.yml
```

```
-
 name: this is a simple html project deploy using ansible
 hosts: workers
 become: true
 tasks:
   - name: install nginx
     apt:
       name: nginx
       state: latest

   - name: start nginx
     service:
       name: nginx
       state: started

   - name: Deploy webpage
     copy:
       src: index.html
       dest: /var/www/html
```

### Deploy and Access

```
sudo ansible-playbook myansible_playbook.yml
```

open your webapp using server-pub-ip

-----------------------------------------------
