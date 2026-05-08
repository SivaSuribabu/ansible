# ansible
This repo contains Ansible 

pip install "ansible>=9,<10"
ansible-galaxy collection install amazon.aws:==7.6.1
ansible-galaxy collection list amazon.aws
ansible-inventory -i aws_ec2.yml --graph

===============================================
aws_ec2.yaml

plugin: amazon.aws.aws_ec2
regions:
  - us-east-1

filters:
  instance-state-name: running

hostnames:
  - private-ip-address

keyed_groups:
  - key: tags.Name
    prefix: tag

================================================


=================================================
plugin: amazon.aws.aws_ec2

regions:
  - us-east-1

filters:
  instance-state-name: running

hostnames:
  - ip-address

compose:
  ansible_host: public_ip_address

vars:
  ansible_user: ec2-user
  ansible_ssh_private_key_file: ~/.ssh/mykey.pem


=================================================
pip install ansible


which python
which ansible
ansible --version
