# Operating System Playground

This repo contains:

* A Vagrantfile for multiple OSes.  
* A docker-compose.yml file for multiple OSes.

It is intended as a playground to learn how different operating systems work and test them out.  Most operating systems have both Intel (amd64) and ARM 64 bit (arm64v8) images available, if so both are included.

You'll need Vagrant and VirtualBox to use the Vagrantfile, or alternatively Docker CE to use the docker-compose.yml. You can install these via the documentation on their websites:

* Vagrant https://www.vagrantup.com/docs/installation/
* VirtualBox https://www.virtualbox.org/wiki/Downloads
* Docker https://docs.docker.com/install/

You need to be running a 64 bit operating system in all cases, and you need virtualization to be enabled in your BIOS. Docker is significantly easier to install and run that Vagrant/VirtualBox, but won't provide you with a full operating system with standard processes the way Vagrant/Virtualbox will. 

* Docker is useful for understanding commands and how the package manager works, which is a subset of what you get with Vagrant/Virtualbox.

* Vagrant/Virtualbox will allow you to work with the bootloader, init system, and services - the full OS experience.

The origin of all images are available in the comments in the Vangrantfile and docker-compose.yml. Where possible, the image provided by the operating system vendor is used, and where it is not possible, the source is another trusted party. For example, HashiCorp provides both Vagrant and the Ubuntu images used by Vagrant.  Any concerns or updates should be filed as issues or pull requests respectively.

Some notes on limitations of Docker and VirtualBox.  These are a snapshot as of June 21, 2023.
* Docker will run on Linux, Windows, and Mac - both Intel/AMD CPU and ARM CPU systems.  
  - Linux containers can run with a different architecture than the underlying hardware. However,
    64 bit containers cannot be run on 32 bit operating systems.
  - Windows containers have to run with the same OS and version as the Windows host.  They won't run on non-Windows (Linux, Mac) hosts.
* Vagrant will run on Linux, Windows, and Mac - both Intel/AMD CPU and ARM CPU systems.   
  - VirtualBox is the default hypervisor.  It will run almost any OS that will run on an emulated version of the underlying hardware. It won't run Intel/AMD architecture Vagrant boxes on Macs with ARM processors.



