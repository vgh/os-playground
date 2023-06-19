# -*- mode: ruby -*-
# vi: set ft=ruby :

# Some command usage:
#   vagrant up # Will download and run all VMs. Don't use this unless
#     you have a lot of time, disk space, and RAM.
#   vagrant up arch # Will download the archlinux/archlinux Vagrant box
#     and run it. The download is first-time-only so further runs will
#     be much faster.  The same command format can be run to bring up 
#     any other defined VM.
#   vagrant status # Will show the status of all of the VMs.
#   vagrant halt # Will halt all VMs.
#   vagrant halt arch # Will halt the 'arch' VM.  The same command 
#     format can be run to halt any other defined VM.
#   vagrant destroy  # Will destroy all VMs. Use this if you've messed
#     them up and want to start over.
#   vagrant destroy arch  # Will destroy the 'arch' VM. The same command 
#     format can be run to destroy any other defined VM.
#   vagrant ssh arch # Will SSH into the 'arch' VM as an user with sudo
#      privileges. The same command format can be run to SSH into any
#      other VM, if it is running (see 'vagrant status'.)
# Note: For whatever reason, arm64 vagrant boxes are not provided by default.
#   And Vagrant does not do CPU aware box handling.  So, all boxes used below 
#   are x86_64 architecture.  See:
#   https://github.com/hashicorp/vagrant/issues/12610
#   ... for some discussion of this.

Vagrant.configure(2) do |config|

  # Standard for all VMs:
  # -> A specified IP on a private network so the VMs can talk to each other.
  # -> Synchronization or mounting of default shared folder is disabled. This
  #    is due to (A) This is a *playground*, and it should be safe for
  #    experimentation. The default synchronized folder could be accidentally 
  #    deleted or could have private information in it that would be 
  #    inappropriate for some modes of experimentation.  
  #    If you want to override this in your own copy, feel free to do so. 
  #    If you do so, note that arch and ubuntu *mount* the directory by 
  #    default, and that the other OSes *rsync* it by default!

  # Due to a bug in Ubuntu
  # See https://bugs.launchpad.net/cloud-images/+bug/1829625
  config.vm.provider 'virtualbox' do |v|
    v.customize ["modifyvm", :id, "--uart1", "0x3F8", "4"]
    v.customize ["modifyvm", :id, "--uartmode1", "file", File::NULL]
  end
   
  # Official Arch Linux box
  config.vm.define("arch") do |arch_config|
    arch_config.vm.hostname = "arch"
    # Source: https://wiki.archlinux.org/index.php/Vagrant
    arch_config.vm.box = "archlinux/archlinux"
    arch_config.vm.network "private_network", ip: "172.25.0.2", netmask: "255.255.0.0"
    # Disable default synced folder
    arch_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Debian 11 (Bullseye) box
  config.vm.define("debian_11") do |debian_11_config|
    debian_11_config.vm.hostname = "debian-11"
    # Source: https://wiki.debian.org/Teams/Cloud/VagrantBaseBoxes
    debian_11_config.vm.box = "debian/bullseye64"
    debian_11_config.vm.network "private_network", ip: "172.25.0.6", netmask: "255.255.0.0"
    # Disable default synced folder
    debian_11_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Debian 12 (Bookworm) box
  config.vm.define("debian_12") do |debian_12_config|
    debian_12_config.vm.hostname = "debian-12"
    # Source: https://wiki.debian.org/Teams/Cloud/VagrantBaseBoxes
    debian_12_config.vm.box = "debian/bookworm64"
    debian_12_config.vm.network "private_network", ip: "172.25.0.7", netmask: "255.255.0.0"
    # Disable default synced folder
    debian_12_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Fedora 37 box
  config.vm.define("fedora_37") do |fedora_37_config|
    fedora_37_config.vm.hostname = "fedora-37"
    # Source: https://developer.fedoraproject.org/tools/vagrant/vagrant-atlas.html
    # Note that the article doesn't mention the most recent releases of Fedora, the same
    # repo referred to there is still in use.
    fedora_37_config.vm.box = "fedora/37-cloud-base"
    fedora_37_config.vm.network "private_network", ip: "172.25.0.10", netmask: "255.255.0.0"
    # Disable default synced folder
    fedora_37_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Fedora 38 box
  config.vm.define("fedora_38") do |fedora_38_config|
    fedora_38_config.vm.hostname = "fedora-38"
    # Source: https://developer.fedoraproject.org/tools/vagrant/vagrant-atlas.html
    # Note that the article doesn't mention the most recent releases of Fedora, the same
    # repo referred to there is still in use.
    fedora_38_config.vm.box = "fedora/38-cloud-base"
    fedora_38_config.vm.network "private_network", ip: "172.25.0.11", netmask: "255.255.0.0"
    # Disable default synced folder
    fedora_38_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

   # Official Kali Linux rolling box
  config.vm.define("kali") do |kali_config|
    kali_config.vm.hostname = "kali"
    # Source: https://www.kali.org/news/announcing-kali-for-vagrant/
    kali_config.vm.box = "kalilinux/rolling"
    kali_config.vm.network "private_network", ip: "172.25.0.15", netmask: "255.255.0.0"
    # Disable default synced folder
    kali_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Rocky Linux 8 (Green Obsidian) box
  config.vm.define("rocky_8") do |rocky_8_config|
    rocky_8_config.vm.hostname = "rocky-8"
    # Source: https://forums.rockylinux.org/t/all-rocky-linux-links/833
    rocky_8_config.vm.box = "rockylinux/8"
    rocky_8_config.vm.network "private_network", ip: "172.25.0.18", netmask: "255.255.0.0"
    # Disable default synced folder
    rocky_8_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Rocky Linux 9 (Blue Onyx) box
  config.vm.define("rocky_9") do |rocky_9_config|
    rocky_9_config.vm.hostname = "rocky-9"
    # Source: https://forums.rockylinux.org/t/all-rocky-linux-links/833
    rocky_9_config.vm.box = "rockylinux/9"
    rocky_9_config.vm.network "private_network", ip: "172.25.0.19", netmask: "255.255.0.0"
    # Disable default synced folder
    rocky_9_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Ubuntu 20.04 (Focal Fossa) box, from HashiCorp
  config.vm.define("ubuntu_2004") do |ubuntu_2004_config|
    ubuntu_2004_config.vm.hostname = "ubuntu-2004"
    ubuntu_2004_config.vm.box = "ubuntu/focal64"
    ubuntu_2004_config.vm.network "private_network", ip: "172.25.0.22", netmask: "255.255.0.0"
    # Disable default synced folder
    ubuntu_2004_config.vm.synced_folder ".", "/vagrant", disabled: true
  end
   
   # Official Ubuntu 22.04 (Jammy Jellyfish) box, from HashiCorp
  config.vm.define("ubuntu_2204") do |ubuntu_2204_config|
    ubuntu_2204_config.vm.hostname = "ubuntu-2204"
    ubuntu_2204_config.vm.box = "ubuntu/jammy64"
    ubuntu_2204_config.vm.network "private_network", ip: "172.25.0.23", netmask: "255.255.0.0"
    # Disable default synced folder
    ubuntu_2204_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

end 
