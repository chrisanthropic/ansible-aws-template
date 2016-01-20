## WHAT
A barebones setup for an Ansible project to manage AWS instances using Ansible's "Dynamic Inventory" script, and is only meant to get you started with Ansible and able to communicate between your local machine and your AWS account.

It assumes you have an AWS account with SSH passwords disabled and .pem logins allowed only.

## HOW
- Git clone this repo.
- Export your AWS keys (or add the commands to your .profile or .bashrc)
    - `export AWS_SECRET_ACCESS_KEY='###'` 
    - `export AWS_ACCESS_KEY_ID='###'`
- Run it
    - `ansible-playbook -i inventory/ec2.py playbook.yml`

## CAUTION
Running this script will create the following resources on your AWS account and YOU COULD BE CHARGED.

RESOURCES:
- 1 local ssh key; ~/.ssh/id_rsa (if it doesn't exist)
- 1 VPC
- 1 VPC Internet Gateway
- 2 subnets
- 2 t2.micro EC2 instances
- 2 EC2 Security Groups