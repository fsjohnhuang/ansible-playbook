# Comment Style
Obey the rules in section Comments and Docstrings of Google Python Style Guide.
   
# Naming Convention
- Playbook File
   - Pattern: `[{project}-[{env}-]]{object}-{verb}.yml`
   - Sample: 
     - `oml-web-deploy.yml`
     - `oh_my_logging-compile.yml`
     - `oml-uat2-api-compile.yml`
- Role Directory Name
   - Pattern: `[{project}-]{object}[-{verb}]`
   - Sample:
     - `web-deploy`
     - `httpd`
- Task File of Roles
   - Pattern: `{object}-{verb}.yml`
   - Sample:
     - `web-deploy.yml`
     - `web_api-compile.yml`
- Inventory File Name
   - Pattern: `{project}-{env}`
   - Sample:
     - `oml-prod`
     - `oml-uat2`
- Content of inventory
  - Sample:
```
# inventories/oml-prod.yml

# Define the hosts information.
[web]
127.0.0.1 ansible_ssh_user="administrator" ansible_ssh_pass="123"
127.0.0.2 ansible_ssh_user="administrator" ansible_ssh_pass="123"
[web_with_f5:children] # Mapping configuration defined in ./group_vars/web_with_f5.yml
web
[prod-web:children] # Mapping configuration defined in  ./group_vars/prod-web.yml
web


# Mapping Windows common configuration defined in ./group_vars/windows.yml
[windows:children]
web
```
- Group Variables File Name
   - Pattern: `{env}-{object}`
   - Sample:
     - `dev-httpd`
     - `prod-web_api`
- Variable
   - Requriement: Upper Case Letters
   - Sample: `{{ ENV }}`
- Name of Task
   - Pattern
     - Display all variables used by task.
     - Must be ends with either full stop or question mark.
       - Full stop means normal statement.
       - Question mark means to get state as input of the follow-up predications.
   - Sample
```yaml
---
     
- name: Directory {{ DEST }} existed?
  file: 
    path: {{ DEST }}
    state: present
  register: DEST_EXISTED

- name: Copy files from {{ SRC }} to {{ DEST }}.
  copy:
    src: {{ SRC }}
    dest: {{ DEST }}
  when: not DEST_EXISTED.existed
```

# Misc
- Donot use `true/false`, use idiom `yes/no` instead.
