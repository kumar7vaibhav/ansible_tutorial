# Tags
We can add tags to the playbooks.

Example
```
 - hosts: all
   become: true
   pre_tasks:
 
   - name: install updates (RedHat)
     tags: always
     yum:
       update_only: yes
       update_cache: yes
     when: ansible_distribution == "RedHat"
```
## List Tags
Command
```
ansible-playbook --list-tags tags.yaml
```
Output
```
playbook: tags.yaml

  play #1 (all): all    TAGS: []
      TASK TAGS: [always]

  play #2 (web_servers): web_servers    TAGS: []
      TASK TAGS: [apache, httpd, rhel, ubuntu]

  play #3 (db_servers): db_servers      TAGS: []
      TASK TAGS: [db, mariadb, rhel, ubuntu]

  play #4 (file_servers): file_servers  TAGS: []
      TASK TAGS: [samba]
```

## Run playbook for only specific tags
Command -
```
ansible-playbook --tags apache --ask-become-pass tags.yaml
```

Command of multiple tags
```
ansible-playbook --tags "rhel,ubuntu" --ask-become-pass tags.yaml
```