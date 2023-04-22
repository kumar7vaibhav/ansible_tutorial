# Starting Services

## Start httpd service on RHEL

```
   - name: start and enable httpd (CentOS)
     tags: apache,centos,httpd
     service:
       name: httpd
       state: started
       enabled: yes
     when: ansible_distribution == "CentOS"
 
```
