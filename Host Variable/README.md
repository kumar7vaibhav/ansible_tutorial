# Host Variables

## Declare the Variables
For RedHat
```ini
apache_package_name: httpd
apache_service: httpd
php_package_name: php
```

For Ubuntu
```ini
apache_package_name: apache2
apache_service: apache2
php_package_name: libapache2-mod-php
```

## Use the Variables
```yaml
# Install httpd on RedHat  
- name: install httpd package (RedHat)
  tags: apache,rhel,httpd
  yum:
    name:
      - "{{  apache_package_name  }}"  # use the variables
      - "{{  php_package_name  }}"
    state: latest
  when: ansible_distribution == "RedHat"

  # Start httpd service on RedHat
- name: start and enable httpd (RedHat)
  tags: apache,centos,httpd
  service:
    name: "{{  apache_service  }}"
    state: started
    enabled: yes
  when: ansible_distribution == "RedHat"

# Install Apache2 on Ubuntu
- name: install apache2 package (Ubuntu)
  tags: apache,ubuntu,httpd
  apt:
    name:
      - "{{  apache_package_name  }}"
      - "{{  php_package_name  }}"
    state: latest
  when: ansible_distribution == "Ubuntu"
```