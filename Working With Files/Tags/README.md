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