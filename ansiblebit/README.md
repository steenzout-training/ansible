# ansiblebit

## what is ansiblebit?

It's the place where I put high quality roles that I develop on my own behalf.


## primogen

I usually use [this repository][ansiblebit.primogen] as the starting point for all my roles:

    $ git clone git@github.com:ansiblebit/primogen.git

It has the following features which we'll review:

- ability to test roles against multiple ansible versions using [tox][tox]
- ability to test roles against multiple OS/releases
- out the box integration with [travis-ci][travis-ci]
- easy configuration of virtual machines
- complete README
- includes a template for debug and validation tasks

[Ansible Galaxy][galaxy] can generate you the structure for a role but
that's where it ends.

You have to setup your [tox.ini][tox], `.travis-yml` file, etc.

[Tox][tox] by itself helps setup the [virtualenv][virtualenv] but
you still need something to make it easy to provision [Vagrant][vagrant] virtual machines,
run playbooks, run tests and check results.

Due to this, I've added a few bash scripts to make it easy to
spawn virtual machines, run playbooks and run tests.

A criteria that I've seen the best role implementations use,
which I also have adopted,
is idempotency testing.

Idempotency in the [Ansible][ansible] context can be explained by simply stating:
'If you successfully run a playbook more than once only
on the first run the playbook will report tasks that changed something on a server (changed > 0).'

If you are careful in maintaining your infrastructure you will,
like me,
use the `--check --diff` options of the `ansible-playbook` book often.

I've noticed that though a playbook / role may pass idempotency tests when
running them in this check mode sometimes they will not be able to complete.

Due to this,
I've also added a test bash script to cover this scenario.

An implementations of [ansiblebit.primogen][ansiblebit.primogen]
can be seen at [ansiblebit.oracle-java][ansiblebit.oracle-java].

Of course there is a better way to implement this than cloning [ansiblebit.primogen][ansiblebit.primogen] but
though it has become more stable I still do some minor tweaks.

Eventually some of the scripts will be put together in a Python library and
the git repositories for the roles can be cleaned up.

Until then, this is the best I can offer with the time that I have.


## Exercise

- clone [ansiblebit.oracle-java][ansiblebit.oracle-java]
- try to run the tests
- try to run the tests using a single ansible version
- try to run the tests using a single ansible version and a single virtual machine
- I'll do a demo of how you can speed the implementation process


[ansible]:                  http://ansible.com                          "Ansible"
[ansiblebit.primogen]:      https://github.com/ansiblebit/primogen/     "ansiblebit.primogen"
[ansiblebit.oracle-java]:   https://github.com/ansiblebit/oracle-java/  "ansiblebit.oracle-java"
[galaxy]:                   https://galaxy.ansible.com/                 "Ansible Galaxy"
[travis-ci]:                http://travis-ci.org/                       "travis-ci"
