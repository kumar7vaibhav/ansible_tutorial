# Task

# Create Sub Directories
```
kvaibhav@VM0:~/ansible1/roles$ tree
.
├── base        
│   └── tasks   
├── db_servers  
│   └── tasks   
├── file_servers
│   └── tasks   
├── web_servers 
│   └── tasks   
└── workstations
    └── tasks   

```
# Roles Playbook
We will refactor all the code in our sites.yaml file into smalller roles and refer those roles in the main file i.e. `sites.yaml`

# Create Tasks
1. Start by making a main file in each sub-directories
` nano base/tasks/main.yaml`
2. Add the refactored content from old playbook. 
```yaml
  # User key added
  - name: add ssh key for alpha
    tags: always
    authorized_key:
      user: alpha
      key: "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAILYzaKsIpIxMxypOkNommg53oSWCkZhxWa+40NYVpn6T ansible"
```
3. Add the files in `files` directory
```
.
├── ansible.cfg
├── base
│   └── tasks
│       └── main.yaml
├── db_servers
│   └── tasks
│       └── main.yaml
├── file_servers
│   └── tasks
│       └── main.yaml
├── inventory
├── sites.yaml
├── web_servers
│   ├── files
│   │   └── default_site.html  
│   └── tasks
│       └── main.yaml
└── workstations
    └── tasks
        └── main.yaml
```
4. Run the roles playbook. `sites.yaml` in this example.
