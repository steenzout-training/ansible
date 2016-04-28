# Inventory

On the previous exercise,
you used `-i localhost,` on the `ansible-playbook` command.

In a real scenario,
you typically use a file which
contains the hosts you wish to run playbooks against.

Obviously,
if the file simply contained all hosts it
would make the task of writing the playbooks
filled with logic to identify which hosts a playbook should target.

This would be error-prone and difficult to maintain.

Ansible provides a way for you to define a file called [inventory][inventory] that
by using a INI format you can specify hosts, host variables,
define group(s) of hosts and group variables.

Review now the Ansible documentation regarding the [inventory][inventory].


## 

Start the Vagrant virtual machine:

    $ vagrant up

Under the `inventory` directory you can find a `hosts` file.

This will be the inventory for this exercise.

Before you apply the playbook to the server,
perform a dry run using:

    $ ansible-playbook --check --diff -i inventory/hosts base.yml

Check what is happening when you use `with_items` and `become`.

Run the playbook:

    $ ansible-playbook --check --diff -i inventory/hosts base.yml

Login to the server and see if you got what you expected.

If you used the generic ssh config you can login to the server using:

    $ ssh -i .vagrant/machines/training.ansible.inventory/virtualbox/private_key training.ansible.inventory

Otherwise use

    $ vagrant ssh


## --limit

Change the playbook to echo the `mygroup` variable.

Set that task with a `debug` tag.

Now run the playbook but only execute tasks with the `debug` tag:

    $ ansible-playbook -i inventory/hosts base.yml --tags=debug

Now limit to `groupA` and then `groupB` and see if there is a difference in the output:

    $ ansible-playbook -i inventory/hosts base.yml --tags=debug --limit groupA

    $ ansible-playbook -i inventory/hosts base.yml --tags=debug --limit groupB

Now change the target on the playbook from `all` to `groupA`.

    $ ansible-playbook -i inventory/hosts base.yml --tags=debug --limit groupA

Check again the difference.


**Warning**: unless you have a very strong use case,
defining as a playbook target a group which contains all hosts,
like `hosts: all`,
is *not* recommended.


## Advanded Exercise: delegation

Destroy the vagrant box and
use an Ansible playbook to bring it back up and
add your ssh public key to the `~vagrant/.ssh/authorized_keys` file.

You can use the [add_host][module_add_host] module,
the [lineinfile][module_lineinfile] and
`delegate_to` on another task.


## Advanced Exercise: delegation with play variation

Try and create two plays on the same playbook.


## ansible-playbook --limit

This `ansible-playbook` option is quite handy in a real-world scenario.


[inventory]:            http://docs.ansible.com/ansible/intro_inventory.html    "inventory"
[module_add_host]:      http://docs.ansible.com/ansible/add_host_module.html    "add_host module"
[module_lineinfile]:    http://docs.ansible.com/ansible/lineinfile_module.html  "lineinfile module"
[module_copy]:          http://docs.ansible.com/ansible/copy_module.html        "copy module"
