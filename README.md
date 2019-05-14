# ansible-base
An ansible playbook to install and configure services for Linux System.
# Requirement:
- Ansible v2.7: https://www.ansible.com/  ( only on control machine).
- Python 2.7. ( both control machine and remote machine).
- Ubuntu 16.04 and Ubuntu 18.04.
- Centos 7.
- SSH services installed.
# HOW TO RUN:
# Edit hosts file:
## Ex:
    [rabbit_master]
    master ansible_host=192.168.2.55 ansible_ssh_user=root ansible_ssh_private_key_file=/home/thanhho/.ssh/id_rsa

- [rabbit_master]: group name of server.
- master: set hostname for server.
- ansible_host: your ip server.
- ansible_ssh_user: your user of server( i used to root).
- ansible_ssh_private_key_file: private key for ssh connections.

# Edit playbook:
## Ex:
    hosts: all
    roles:
     - base
     - mongodb

- hosts:all (for all group listed in hosts file, you can set group name for playbook to run only hosts listed in group).
- roles: simply list roles( services) to run in this playbook.

# COMMAND TO RUN PLAYBOOK:
- ansible-playbook -i hosts playbook file

# NOTE:
- Keep **group name** in host file, not recommend to change them.If changed, must be changed config in roles.
- Focus to default/main.yml and vars/<any file>.yml in **<role name>**
