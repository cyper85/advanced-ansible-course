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
Change the DB-IP-Address in `/vars/http_server.yml`

```bash
cd ~/advanced-ansible-course
ansible-playbook install-playbook.yml -i inventory.txt --extra-vars "ansible_sudo_pass=osboxes.org" --ask-vault-pass
```

vault-password is `osboxes.org`

Server are started on both http-targets.

## Loadbalancer
I installed the loadbalancer on the ansible-controller-host

```bash
ansible-playbook setup-loadbalancer.yml --extra-vars "ansible_sudo_pass=osboxes.org"
```

At the end, you can call http://{ansible-controller-host-ip}:80 and see on of the http_server.