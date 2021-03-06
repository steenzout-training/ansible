# Vagrant

This part of the training will do a quick overview of
the [Vagrant][vagrant] commands you will be using.

[Vagrant][vagrant] provides an [Ansible][ansible] provisioner but
the goal of the current exercise is for you to get acquainted with
the [Vagrant][vagrant] commands.


## Vagrantfile

In order to spawn a [vagrant][vagrant] box
you'll need to have a `Vagrantfile`.

You can generate a brand new `Vagrantfile` by using the following command:

    vagrant init

In this directory you will find a `Vagrantfile.init`
which is the result of the issuing the command above.

You can find a more readable example on `Vagrantfile`
which we'll use to get you acquainted with [vagrant][vagrant].

More information on `Vagrantfile` can be found [here](https://www.vagrantup.com/docs/vagrantfile/).


## Commands

### vagrant up

This command will download the image and start the virtual machine.


### vagrant status

This command presents the state of each virtual machine defined in the `Vagrantfile`.


### vagrant ssh

This command will enable to login to the virtual machine.

Do the following commands:

    $ cat /proc/cpucount
    $ cat /proc/meminfo

Compare the number of CPUs and memory available
with the settings from the `Vagrantfile`.

The same result will happen if you use `vagrant ssh training.ansible`.


### vagrant ssh-config

Use this command to see how you can setup your `~/.ssh/config` file
to login to this virtual machine using ssh.
    
    Host training.ansible
      HostName 127.0.0.1
      User vagrant
      Port 2222
      UserKnownHostsFile /dev/null
      StrictHostKeyChecking no
      PasswordAuthentication no
      IdentityFile "..some_path../ansible/vagrant/.vagrant/machines/training.ansible/virtualbox/private_key"
      IdentitiesOnly yes
      LogLevel FATAL

Now you do:

    $ ssh training.ansible

And it should just work.

**Note**: compare the speed of doing `vagrant ssh` with `ssh training.ansible`.

**Recommendation**: use a custom name for your virtual machines.
The codename of Linux distribution is a good candidate: `config.vm.define 'trusty' do |host|`.
For more complex setups you may want to use some type of namespace convention.

**Recommendation**: use a more generic ssh config to avoid needed to update your `~/.ssh/config` file often.
For example:

    Host training.*
        HostName 127.0.0.1
        IdentitiesOnly yes
        LogLevel FATAL
        PasswordAuthentication no
        Port 2222
        StrictHostKeyChecking no
        User vagrant
        UserKnownHostsFile /dev/null

Meaning you could login using something like:

    ssh -i ..some_path../ansible/vagrant/.vagrant/machines/training.ansible/virtualbox/private_key training.ansible

### vagrant destroy

Destroys the virtual machine.


## Links

- [Using Vagrant and Ansible][ansible_vagrant]
- [Vagrant][vagrant]


[ansible_vagrant]:  http://docs.ansible.com/ansible/guide_vagrant.html  "Using Vagrant and Ansible"
[vagrant]:          https://www.vagrantup.com/                          "Vagrant"
