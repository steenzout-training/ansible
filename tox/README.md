# tox

[Tox][tox] is a [virtualenv][virtualenv] and test command line tool for [Python][python].


## Advantages

With [tox][tox] you have a declarative and
easily reproducible way of creating [virtualenv][virtualenv] environments.

This very important when you want to
replicate a test environment between
your laptop and your build / development / staging / production environment.

When you are developing a role,
this tool, together with a test playbook,
can give you enables you to easily test across several [Ansible][ansible] versions.

Since playbooks change your infrastructure,
running a playbook with a new version without testing it and
its roles with a different [Ansible][ansible] version can
lead to unexpected and catastrophic results.

[Ansible][ansible] is still a software,
it has bugs and from version to version,
inventory parsing behavior may change and
module behavior as well.

Reading all the release notes and
all of the new documentation is not
how anyone should guarantee that playbooks and roles
behave in the same manner.

Testing is.


## 

[Tox][tox] by itself helps setup the [virtualenv][virtualenv] but
you still need something to make it easy to provision [Vagrant][vagrant] virtual machines,
run playbooks, run tests and check results.

Two examples of how to do this can be seen at:

- [ansiblebit.oracle-java][ansiblebit.oracle-java]
- [ansiblebit.primogen][ansiblebit.primogen]



- review the code
- run a test on a single VM
- run tests on all VMs

[ansible]:                  http://ansible.com                          "ansible"
[ansiblebit.oracle-java]:   https://github.com/ansiblebit/oracle-java   "ansiblebit.oracle-java"
[tox]:                      http://tox.readthedocs.io/en/latest/        "tox"
[virtualenv]:               https://virtualenv.pypa.io/en/latest/       "virtualenv"
