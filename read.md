# ansible-jenkins
*Ansible Installation and configuration*:
- Lab Setup:

. Create one ubuntu 22.04 instance

. AWS machines have passwords disabled by default.

. So lets enable password
In this /etc/ssh/sshd_config  => PasswordAuthentication no => yes
- Restart sshd service

sudo systemctl restart sshd
Lets create a user called as devops with password as devops on  Anisble control
- sudo adduser devops

Now logout and check for password authentication.
Lets add sudo permissions for devops user. 

- login as ubuntu user

sudo visudo 

devops ALL=(ALL:ALL) NOPASSWD:ALL
then using this command sudo apt update

Login into ansible control node and install ansible Refer Here for the official documentation and Refer Here for installation steps

* sudo apt update

* sudo apt install software-properties-common

* sudo add-apt-repository --yes --update ppa:ansible/ansible

* sudo apt install ansible -y

* ansible --version*

*installing jenkins on smae control node*
refer link 
https://www.jenkins.io/doc/book/installing/linux/


Now lets create a inventory file called as hosts
172.31.3.19
check for host connecting or not
using this command 
Install ansible on the control node

* ansible -i hosts -m ping -k all
![Alt text](2023-02-01%20(3).png)

ansible-playbook

---
- name: installing apache2
  become: yes
  hosts: localhost
  tasks:
    - name: install apache and update packages
      ansible.builtin.apt:
        name: apache2
        update_cache: yes
        state: present
    - name: restart apache
      ansible.builtin.systemd:
        name: apache2
        enabled: yes
        state: started */


