# Ansible_Assignment1
ad hoc commands

commands:

# for creating the group
ansible web -i inventory.ini -m group -a "name=team1 state=present" --become

# for adding a user into a group with home dir 
ansible all -i inventory.ini -m user -a "name=nitish groups=team1 append=yes state=present create_home=yes shell=/bin/bash" --become

#provide the permissions
ansible all -i inventory.ini -m file -a "path=/home/nitish/Team owner=nitish group=team1 mode=770 state=directory" --become

#create a user ninja
ansible all -i inventory.ini -m group -a "name=ninja state=present" --become

#provide the permission
ansible all -i inventory.ini -m file -a "path=/home/nitish/Ninja owner=nitish group=ninja mode=770 state=directory" --become

#additional features:
ansible all -i inventory.ini -m user -a "name=nitish shell=/bin/zsh" --become
ansible all -i inventory.ini -m user -a "name=nitish state=absent remove=yes" --become
ansible all -i inventory.ini -m group -a "name=team1 state=absent" --become
ansible all -i inventory.ini -m shell -a "cut -d: -f1 /etc/group" 
