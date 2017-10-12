# Tutorial Materials

This repository contains materials useful for working through the Paradrop
edge computing tutorial.

## Running the Virtual Machine

We have provided a Vagrantfile so that everyone can have a consistent
development environment during the tutorial, regardless of the operating
system installed on you laptop.

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

## SSH Keys

There will be a few tasks during the tutorial that require you to have an
RSA key set up for SSH authentication. As part of the Vagrant provisioning
process, your VM will automatically generate a unique key. You may have
noticed the public key output at the end of the `vagrant up` command.

You can view the contents of your public key with the following command:

    cat /home/ubuntu/.ssh/id_rsa.pub

### Preparing Your GitHub Account

During the tutorial, we will be writing some code and publishing it on
GitHub (https://github.com).  First, make sure you have a GitHub account. It
is free and only takes an email address to set up.

Next, in order to push code from your VM, you will need to add your SSH
public key to your GitHub profile. That enables GitHub to verify that
the push came from you and not an imposter.

Go to your GitHub account settings page (https://github.com/settings/keys)
and add the **public** key mentioned above.

After you finish the tutorial and/or delete the VM image, feel free to
remove the public key from your account as it will no longer be used.

### Enabling SSH Access to Your Router

During the tutorial, you will be doing some hands-on activitiies with a
Paradrop wireless router. You can use SSH to view and debug software
on the Paradrop router. For security purposes, password authentication
is disabled, so you will need to upload your public key to the router
to enable RSA authentication.

You will be assigned a router to use during the tutorial. After you
receive your router, run this command to enable SSH access with your key.

    pdtools device <address> sshkeys add /home/ubuntu/.ssh/id_rsa.pub

Replace "&lt;address&gt;" with the IP address of your router, which if you are
connected to the Paradrop router's Wi-Fi network, will be "192.168.1.1".

## Other Resources

Check the link below for the latest version of the tutorial instructions. We
recommend reading through sections 1 and 2 before the tutorial.

https://docs.google.com/document/d/1oMEZUYhrmTxA06Cx5Gn9mDtgKnn4OGTc2Qx-uDD9x4M

View our developer-oriented documentation:

http://paradrop.readthedocs.io/en/latest/
