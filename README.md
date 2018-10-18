# Tutorial Materials

This repository contains materials useful for working through the Paradrop
edge computing tutorial. We ask that you review these instructions during
the week leading up to the tutorial so that everyone arrives prepared.

## Running the Virtual Machine

During the tutorial we will be doing some individual programming tasks.
For these exercises, everyone will need to use their own laptop. Because
it is difficult for us to support all of the various operating systems
that people may be running, we have prepared a virtual machine image
for everyone to use as the development environment.

You will need the Vagrantfile in this repository and to have VirtualBox
and Vagrant installed on your laptop

### Install VirtualBox

If you are running Ubuntu:

    sudo apt-get install -y virtualbox

Otherwise, check the VirtualBox download page:
https://www.virtualbox.org/wiki/Downloads

### Install Vagrant

If you are running Ubuntu:

    sudo apt-get install -y vagrant

Otherwise, head over to the Vagrant download page:
https://www.vagrantup.com/downloads.html

### Run the Virtual Machine

Clone this repository, and inside the directory containing the
Vagrantfile, run:

    vagrant up

Then use the SSH command to open a shell inside the VM.

    vagrant ssh

You can use this shell to run all of the commands in the Paradrop
tutorial. Various command line utilities including git, pdtools, and
vim are preinstalled.

### Cleaning Up

Exit the SSH session in the VM with either the 'exit' command or by
typing Ctrl+d.

To stop the VM but leave its files in place for a future development
session:

    vagrant halt

To stop the VM and remove its files:

    vagrant destroy

Finally, if you do not expect to use vagrant again soon, you can delete
the Ubuntu disk image that it downloaded.

    vagrant box remove ubuntu/xenial64

## SSH Keys

There will be a few tasks during the tutorial that require you to have an
RSA key set up for SSH authentication. As part of the Vagrant provisioning
process, your VM will automatically generate a unique key. You may have
noticed the public key output at the end of the `vagrant up` command.

You can view the contents of your public key with the following command:

    cat /home/ubuntu/.ssh/id_rsa.pub

If you receive the error:

    cat /home/ubuntu/.ssh/id_rsa.pub: No such file or directory

You can create one manually with the following command:

	ssh-keygen -A

### Preparing Your Paradrop Developer Account

During the tutorial, you will be interacting with our edge computing
cloud controller at paradrop.org. You should create a free developer
account using your email address.

In order to push code from your VM development environment to our
hosted git repository, you will need to add your SSH public key to your
paradrop.org profile. Your public key allows our system to securely
verify the commits came from you.

Go to your Paradrop Account Settings page
(https://paradrop.org/settings/sshKeys) and add the **public** from your
development environment mentioned in the previous section.

After you finish the tutorial and/or delete the VM image, feel free to
remove the public key from your account as it will no longer be used.

### Enabling SSH Access to Your Router

During the tutorial, you will be doing some hands-on activitiies with a
Paradrop compute node. You can use SSH to view and debug software
on the Paradrop node. For security purposes, password authentication
is disabled, so you will need to upload your public key to the node
to enable RSA authentication.

If you run `pdtools wizard` during the tutorial and answer "yes" to the
question asking if you have a node to configure, it will automatically
try to set up SSH access for you. If you need to enable SSH access later
on, you can run the following command.

    pdtools node --target <address> import-ssh-key ~/.ssh/id_rsa.pub

Replace "&lt;address&gt;" with the IP address or domain name of your
node, which if you are connected to the Paradrop Wi-Fi network, will be
"192.168.1.1".

## Other Resources

Check the link below for the latest version of the tutorial
instructions. We recommend reading through sections 1 and 2 before
the tutorial. Sections 3 and 4 require access to a Paradrop node,
so we will work through those during the tutorial.

https://docs.google.com/document/d/1oMEZUYhrmTxA06Cx5Gn9mDtgKnn4OGTc2Qx-uDD9x4M

For additional information, refer to our developer-oriented system
documentation:

http://paradrop.readthedocs.io/en/latest/
