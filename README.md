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

pip install ansible


which python
which ansible
ansible --version
