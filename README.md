# Assignment
for https://vkb.udemy.com/course/learn-ansible-advanced/

## Requirement

* 4 hosts in [virtualboxes](https://www.virtualbox.org/) with centos 8 (image from [osboxes.org](https://osboxes.org))
* 3 targethosts with IP in `inventory.txt`, grouped to two http hosts and one db host

## Usage
```bash
# shell on ansible-controller
# install ssh-key to all target
ssh-keygen
ssh-copy-id {ip-target1}
ssh-copy-id {ip-target2}
ssh-copy-id {ip-target3}

# install ansible
dnf install -y epel-release git
dnf install -y ansible

# clone repo
git clone git@github.com:cyper85/advanced-ansible-course.git
```

Change the IP-Addresses in `inventory.txt` to the correct ones

```bash
cd ~/advanced-ansible-course
ansible-playbook install-playbook.yml -i inventory.txt --extra-vars "ansible_sudo_pass=osboxes.org"
```

Server are started on both http-targets.

_TODO: loadbalancer_