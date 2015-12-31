## WHAT
A barebones setup for an Ansible project to manage AWS instances using Ansible's "Dynamic Inventory" script, and is only meant to get you started with Ansible and able to communicate between your local machine and your AWS account.

It assumes you have an AWS account with SSH passwords disabled and .pem logins allowed only.

## HOW
- Git clone this repo.
- Export your AWS keys (or add the commands to your .profile or .bashrc)
    - `export AWS_SECRET_ACCESS_KEY='###'` 
    - `export AWS_ACCESS_KEY_ID='###'`
- Edit ansible.cfg with your information
    - Change `private_key_file = ~/.ssh/YOURKEY.pem` to the location of the .pem file you use to SSH into AWS.
    - Change `remote_user = ubuntu` if you use an AMI that doesn't have the ubuntu user (non Ubuntu AMIs).
    - Change `inventory = LOCATION-OF-THIS-REPO/inventory` to the actual location of this repo on your machine.
    - Change `hostfile = LOCATION-OF-THIS-REPO/inventory/ec2.py` to the actual location of this repo on your machine.

## BASIC USE
For simplicity, make sure you enter these commands from the `LOCATION-OF-THIS-REPO/inventory` directory.

**List all EC2 instances**
  `./ec2.py --list`
  
**List Instances in a Specific Region**
    `ansible us-east-1 -m ping`

**List Instances With a Specific Tag**
    `ansible tag_Name_CodeDeploy_dev`

**List Instances Assigned to a Specific Security Group**
    `ansible security_group_fakename -m ping`

**List All of your EC2 Instaces**
    `ansible ec2 -m ping`
    
**List All Instaces of a Specific Type**
    `ansible type_m1_small -m ping`

## FURTHER READING
- My original blog [post](http://www.chrisanthropic.com/blog/2015/getting-started-with-arch-linux-and-ansible/) that turned into this tiny project.
- Ansible [Documentation](http://docs.ansible.com/)
- Ansible [Dynamic Inventory](http://docs.ansible.com/ansible/intro_dynamic_inventory.html#example-aws-ec2-external-inventory-script)

## ToDo
???