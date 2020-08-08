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
#      other VM, if it is running (see 'vagrant status'.
   
Vagrant.configure(2) do |config|

  # Standard for all VMs:
  # -> A specified IP on a private network so the VMs can talk to each other.
  # -> Synchronization or mounting of default shared folder is disabled. This
  #    is due to (A) This is a *playground*, and it should be safe for
  #    experimentation. The default synchronized folder could be accidentally 
  #    deleted or could have private information in it that would be 
  #    inappropriate for some modes of experimentation.  
  #    If youwant to override this in your own copy, feel free to do so. 
  #    If you do so, note that arch and ubuntu *mount* the directory by 
  #    default, and that the other OSes *rsync* it by default!

  # Due to a bug in Ubuntu 19.04 and 20.04
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

  # Official CentOS 6 box
  config.vm.define("centos_6") do |centos_6_config|
    centos_6_config.vm.hostname = "centos-6"
    # Source: https://blog.centos.org/2018/05/updated-centos-vagrant-images-available-v1804-02/
    centos_6_config.vm.box = "centos/6"
    centos_6_config.vm.network "private_network", ip: "172.25.0.3", netmask: "255.255.0.0"
    # Disable default synced folder
    centos_6_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official CentOS 7 box
  config.vm.define("centos_7") do |centos_7_config|
    centos_7_config.vm.hostname = "centos-7"
    # Source: https://blog.centos.org/2018/05/updated-centos-vagrant-images-available-v1804-02/
    centos_7_config.vm.box = "centos/7"
    centos_7_config.vm.network "private_network", ip: "172.25.0.4", netmask: "255.255.0.0"
    # Disable default synced folder
    centos_7_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

   # Official CentOS 8 box
  config.vm.define("centos_8") do |centos_8_config|
    centos_8_config.vm.hostname = "centos-8"
    # Source: https://blog.centos.org/2018/05/updated-centos-vagrant-images-available-v1804-02/
    # Note that although the post doesn't mention CentOS 8, the same repo is used for 6, 7
    # and 8.
    centos_8_config.vm.box = "centos/8"
    centos_8_config.vm.network "private_network", ip: "172.25.0.5", netmask: "255.255.0.0"
    # Disable default synced folder
    centos_8_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Debian 9 (Stretch) box
  config.vm.define("debian_9") do |debian_9_config|
    debian_9_config.vm.hostname = "debian-9"
    # Source: https://wiki.debian.org/Teams/Cloud/VagrantBaseBoxes
    debian_9_config.vm.box = "debian/stretch64"
    debian_9_config.vm.network "private_network", ip: "172.25.0.6", netmask: "255.255.0.0"
    # Disable default synced folder
    debian_9_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Debian 10 (Buster) box
  config.vm.define("debian_10") do |debian_10_config|
    debian_10_config.vm.hostname = "debian-10"
    # Source: https://wiki.debian.org/Teams/Cloud/VagrantBaseBoxes
    debian_10_config.vm.box = "debian/buster64"
    debian_10_config.vm.network "private_network", ip: "172.25.0.7", netmask: "255.255.0.0"
    # Disable default synced folder
    debian_10_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Fedora 31 box
  config.vm.define("fedora_31") do |fedora_31_config|
    fedora_31_config.vm.hostname = "fedora-31"
    # Source: https://developer.fedoraproject.org/tools/vagrant/vagrant-atlas.html
    # Note that the article doesn't mention the most recent releases of Fedora, the same
    # repo referred to there is still in use.
    fedora_31_config.vm.box = "fedora/31-cloud-base"
    fedora_31_config.vm.network "private_network", ip: "172.25.0.8", netmask: "255.255.0.0"
    # Disable default synced folder
    fedora_31_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Fedora 32 box
  config.vm.define("fedora_32") do |fedora_32_config|
    fedora_32_config.vm.hostname = "fedora-32"
    # Source: https://developer.fedoraproject.org/tools/vagrant/vagrant-atlas.html
    # Note that the article doesn't mention the most recent releases of Fedora, the same
    # repo referred to there is still in use.
    fedora_32_config.vm.box = "fedora/32-cloud-base"
    fedora_32_config.vm.network "private_network", ip: "172.25.0.9", netmask: "255.255.0.0"
    # Disable default synced folder
    fedora_32_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

   # Official Kali Linux rolling box
  config.vm.define("kali") do |kali_config|
    kali_config.vm.hostname = "kali"
    # Source: https://www.kali.org/news/announcing-kali-for-vagrant/
    kali_config.vm.box = "kalilinux/rolling"
    kali_config.vm.network "private_network", ip: "172.25.0.10", netmask: "255.255.0.0"
    # Disable default synced folder
    kali_config.vm.synced_folder ".", "/vagrant", disabled: true
  end
   
  # Official Ubuntu 16.04 (Xenial) box, from HashiCorp
  config.vm.define("ubuntu_1604") do |ubuntu_1604_config|
    ubuntu_1604_config.vm.hostname = "ubuntu-1604"
    ubuntu_1604_config.vm.box = "ubuntu/xenial64"
    ubuntu_1604_config.vm.network "private_network", ip: "172.25.0.11", netmask: "255.255.0.0"
    # Disable default synced folder
    ubuntu_1604_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

  # Official Ubuntu 18.04 (Bionic) box, from HashiCorp
  config.vm.define("ubuntu_1804") do |ubuntu_1804_config|
    ubuntu_1804_config.vm.hostname = "ubuntu-1804"
    ubuntu_1804_config.vm.box = "ubuntu/bionic64"
    ubuntu_1804_config.vm.network "private_network", ip: "172.25.0.12", netmask: "255.255.0.0"
    # Disable default synced folder
    ubuntu_1804_config.vm.synced_folder ".", "/vagrant", disabled: true
  end
   
   # Official Ubuntu 20.04 (Focal) box, from HashiCorp
  config.vm.define("ubuntu_2004") do |ubuntu_2004_config|
    ubuntu_2004_config.vm.hostname = "ubuntu-2004"
    ubuntu_2004_config.vm.box = "ubuntu/focal64"
    ubuntu_2004_config.vm.network "private_network", ip: "172.25.0.13", netmask: "255.255.0.0"
    # Disable default synced folder
    ubuntu_2004_config.vm.synced_folder ".", "/vagrant", disabled: true
  end

end 
