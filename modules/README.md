# Modules

Now without the inital setup,
try and create the inventory and a playbook which will
use the following modules:
- [template module][module_template]
- [git module][module_git]
- [user module][module_user]
- [group module][module_group]
- [shell module][module_shell]


Another alternative would be to try and implement a playbook to:
- setup your laptop
- setup a database on a VM
- setup a web server on a VM

A list of all modules can be found [here][all].


[all]:                      http://docs.ansible.com/ansible/modules_by_category.html    "all"
[module_authorized_key]:    http://docs.ansible.com/ansible/authorized_key_module.html  "authorized_key module"
[module_blockinfile]:       http://docs.ansible.com/ansible/blockinfile_module.html     "blockinfile module"
[module_command]:           http://docs.ansible.com/ansible/command_module.html         "command module"
[module_git]:               http://docs.ansible.com/ansible/git_module.html             "git module"
[module_group]:             http://docs.ansible.com/ansible/group_module.html           "group module"
[module_script]:            http://docs.ansible.com/ansible/script_module.html          "script module"
[module_shell]:             http://docs.ansible.com/ansible/shell_module.html           "shell module"
[module_template]:          http://docs.ansible.com/ansible/template_module.html        "template module"
[module_user]:             http://docs.ansible.com/ansible/user_module.html             "user module"
