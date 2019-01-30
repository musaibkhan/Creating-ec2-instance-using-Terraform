# Creating-ec2-instance-using-Terraform
Create a Ec2 instancs using Terraform 
Download terraform zip file 

curl -O https://releases.hashicorp.com/terraform/0.11.1/terraform_0.11.1_linux_amd64.zip
check terraform --version


run terraform init


This is the code for creating Ubuntu Instance 

save this code in .tf format

provider "aws" {
  access_key = "xxxxxxx"
  secret_key = "xxxxxx"
  region     = "us-east-2"
}

resource "aws_instance" "linux" {
  ami           = "ami-0653e888ec96eab9b"
  instance_type = "t2.micro"
  count=2
}

save this file .tf

run terraform plan 

run terraform apply


After creating 2 ubuntu machine using terraform 
Install ansible 

apt-get install ansible

generate ssh key 

copy to  host

once ssh connection is build

Entry hosts name in /etc/ansible/hosts

check your ssh host make sure it wont ask for password 

you can deploy any package to host machine

Step 1:- crete name.yml  

- name: Install base packages
  apt: name={{ item }} state=installed
  with_items:
    - nvm
    - node
    - docker
    - docker compose
    - git
    - openssl
     tags:
    - packages

