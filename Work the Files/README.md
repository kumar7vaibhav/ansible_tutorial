# Working With Files

Copy file from a directory to other
```
    - name: copy default html file for site
    tags: apache,apache2,httpd
    copy: 
        src: default_site.html
        dest: /var/www/html/index.html
        owner: root
        group: root
        mode: 0644
```
Run the Playbook

Check the web server file system
```
[kvaibhav@VM5 ~]$ cat /var/www/html/index.html 
<html>
    <title>Web Site Title</title> 
    <body>
        <p>Ansible is working!</p>
    </body>
</html>
```
Check with `curl`
```
kvaibhav@VM1:~$ curl 10.32.53.5
<html>
    <title>Web Site Title</title> 
    <body>
        <p>Ansible is working!</p>
    </body>
</html>
```

# Uzip and Install Terraform

```
 - hosts: workstations
   become: true
   tasks:

   - name: install unzip
     package:
       name: unzip
 
   - name: install terraform
     unarchive:
      src: https://releases.hashicorp.com/terraform/0.12.28/terraform_0.12.28_linux_amd64.zip
       dest: /usr/local/bin
       remote_src: yes
       mode: 0755
       owner: root
       group: root
```
Output
```
TASK [install unzip] ****************************************************************************
changed: [10.32.53.4]

TASK [install terraform] ************************************************************************
changed: [10.32.53.4]
```