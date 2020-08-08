# Operating System Playground

This repo contains:

* A Vagrantfile for multiple OSes.  
* A docker-compose.yml file for multiple OSes.

It is intended as a playground to learn how different operating systems work and test them out.

You'll need Vagrant and VirtualBox to use the Vagrantfile, or alternatively Docker CE to use the docker-compose.yml. You can install these via the documentation on their websites:

* Vagrant https://www.vagrantup.com/docs/installation/
* VirtualBox https://www.virtualbox.org/wiki/Downloads
* Docker https://docs.docker.com/install/

You need to be running a 64 bit operating system in all cases, and you need virtualization to be enabled in your BIOS. Docker is significantly easier to install and run that Vagrant/VirtualBox, but won't provide you with a full operating system with standard processes the way Vagrant/Virtualbox will. 

* Docker is useful for understanding commands and how the package manager works, which is a subset of what you get with Vagrant/Virtualbox.

* Vagrant/Virtualbox will allow you to work with the bootloader, init system, and services - the full OS experience.

The origin of all images are available in the comments in the Vangrantfile and docker-compose.yml. Where possible, the image provided by the operating system vendor is used, and where it is not possible, the source is another trusted party. For example, HashiCorp provides both Vagrant and the Ubuntu images used by Vagrant.  Any concerns or updates should be filed as issues or pull requests respectively.


