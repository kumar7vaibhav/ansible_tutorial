# Adding Users

## Create User
```
- hosts: all
  become: true
  tasks:

  - name: create alpha user
    tags: always
    user:
      name: alpha
      group: root
```

Output
```
[kvaibhav@VM5 ~]$ cat /etc/passwd | grep ^alpha
alpha:x:1001:0::/home/alpha:/bin/bash
```

## Add the Authorized Key
```
- name: add ssh key for alpha
    tags: always
    authorized_key:
      user: alpha
      key: "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAILYzaKsIpIxMxypOkNommg53oSWCkZhxWa+40NYVpn6T ansible"
```
## Make user root/sudo
```
  # Make alpha sudo/root
  - name: add sudoers file for alpha
    copy: 
      src: sudoer_alpha
      dest: /etc/sudoers.d/alpha
      owner: root
      group: root
      mode: 0440
```

### Check Permission
SSH Into other machine
```
kvaibhav@VM0:~/ansible1/add_users$ ssh -i ~/.ssh/ansible/ansible alpha@10.32.53.10
Activate the web console with: systemctl enable --now cockpit.socket

Register this system with Red Hat Insights: insights-client --register
Create an account or view all your systems at https://red.ht/insights-dashboard
```

Run a command with sudo.
```
[alpha@VM5 ~]$ sudo yum update
Last metadata expiration check: 0:02:09 ago on Sat Apr 22 12:24:37 2023.
Dependencies resolved.
Nothing to do.
Complete!
```

# Using Remote User
Change the `ansible.cfg`
```
[defaults]
inventory = inventory
private_key_file = ~/.ssh/ansible/ansible
remote_user = alpha
```
Now run `ansible-playbook adding_users.yaml`
You no longer need the `--ask-become-pass`

