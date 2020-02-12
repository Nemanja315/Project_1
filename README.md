---
- name: First Play
  hosts: routers
  gather_facts: False
  connection: local
  tasks:
   - name: First Task
     ios_command:
         commands: show ip int br
     register: version
   - name: Second Task
     debug:
       var: version
   - name: Third Task
     copy:
       content: "{{ version.stdout[0] }}"
       dest: "/home/ansible/lab1/backups/show_run.txt"
