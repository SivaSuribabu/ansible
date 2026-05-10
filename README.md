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
  "tag:Monitoring": "Yes"

hostnames:
  - private-ip-address

compose:
  ansible_user: ubuntu
  ansible_ssh_private_key_file: /home/ubuntu/.ssh/id_rsa


=================================================
pip install ansible


which python
which ansible
ansible --version


for host in $(ansible-inventory -i aws_ec2.yml --list | jq -r '._meta.hostvars | keys[]'); do
    ssh-keyscan -H $host >> ~/.ssh/known_hosts 2>/dev/null
done
ansible all -i aws_ec2.yml -m ping

