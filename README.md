# Tutorial Materials

This repository contains materials useful for working through the Paradrop
edge computing tutorial.

## Virtual Machine Image

We have provided a Vagrantfile so that everyone can have a consistent
development environment during the tutorial, regardless of the operating
system installed on you laptop.

### Install Vagrant

If you are running Ubuntu:

    sudo apt-get install -y vagrant

Otherwise, head over to the Vagrant download page:
https://www.vagrantup.com/downloads.html

### Install VirtualBox

If you are running Ubuntu:

    sudo apt-get install -y virtualbox

Otherwise, check the VirtualBox download page:
https://www.virtualbox.org/wiki/Downloads

### Run the Virtual Machine

Check out this repository and from the same directory as the Vagrantfile,
run:

    vagrant up

Then use SSH to open a shell inside the VM.

    vagrant ssh

You can use this shell to run all of the commands in the Paradrop
tutorial.

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

## Resources

For the latest version of the tutorial document:

https://docs.google.com/document/d/1oMEZUYhrmTxA06Cx5Gn9mDtgKnn4OGTc2Qx-uDD9x4M

View our developer-oriented documentation:

http://paradrop.readthedocs.io/en/latest/
