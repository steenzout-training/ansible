# ansible-playbook

This command is what will enable you to
perform changes on servers.

For the purpose of this exercise,
we are going to simply use your workstation.

In order to run this command you need to have YAML file
with a specific structure
which we'll call _the playbook_.

On this directory you will find a `site.yml` file
which will be the playbook for this exercise.

Since this is YAML note that:

- the play is an element of a list
- play data structure is a hash composed with key/value pairs
- the keys for play attributes (`name`, `hosts`, etc...) only have values
- the task executions sections keys (`pre_tasks`, `roles`, `tasks`, `post_tasks`) have lists as their values

For now, the important parts to pay attention while executing the playbook are:

- definition of the target for this playbook: `hosts: localhost`
- task execution sections (which are written by the order of their execution)
    - `pre_tasks`
    - `roles`
    - `tasks`
    - `post_tasks`

Regarding `myrole`,
for now,
just look at its tasks which are defined under `myrole/tasks`.

You can run this playbook in the following way:

    $ ansible-playbook -i localhost, site.yml

Now run it again:

    $ ansible-playbook -i localhost, site.yml

On the second run you should see:

    localhost                  : ok=4    changed=0    unreachable=0    failed=0

You can test if the directory is there with:

    $ test -d /tmp/steenzout-training.ansible.ansible-playbook \
        && echo 'Directory is there' || \
        echo 'Directory is NOT there'

**Recommendation**: always keep the internal structure of a play as it is shown in `site.yml` so
that you don't get a surprise task getting executed because
you didn't completely/carefully read the playbook.


## Tasks

To execute a task you have to use Ansible modules.

Here goes the links to the [debug][module_debug] and [file][module_file] modules.

Add, remove, change some of the parameters and see what happens.


## Ghost task

Did you notice that there is a certain task that is not being executed?

Try this:

    $ ansible-playbook -i localhost, -e extra=value site.yml

What happened?

This is an example how you can define variables through the command line.


## --tags

Check the `--tags` option.


## --check

Check the `--check` option.


## --diff

Check the `--diff` option.


[module_debug]:     http://docs.ansible.com/ansible/debug_module.html   "debug module"
[module_file]:      http://docs.ansible.com/ansible/file_module.html    "file module"
