---

tags: 
  - guest:-80
  - host:-8080
  - "/vagrant"
  - Chef
  - Docker

---
Below useful command for different Linux stuff.

## Terminator Keyboard Shortcut

![[./_resources/Linux.resources/Screenshot from 2024-06-07 16-31-46.png]]

|     |     |
| --- | --- |
| ```<br>sudo dpkg -r PACKAGE_NAME<br>``` | remove .deb package |
| sudo dpkg -i PACKAGE\_NAME | install .deb package |
| ```<br>sudo apt purge <name_prog><br>``` | uninstall prog |

|     |     |
| --- | --- |
| Begin search | Ctrl+Shift+F |
| System specific | cat /etc/os-release |
| create token to access local cluster microk8s\` | token=$(microk8s kubectl -n kube-system get secret \| grep default-token \| cut -d " " -f1)<br>microk8s kubectl -n kube-system describe secret $token |

# VM Ubuntu con Virtualbox e Vagrant

![[./_resources/Linux.resources/Screenshot from 2024-06-13 16-40-28.png]]
Vogliamo due VM runnate su Virtualbox configurate tramite Vagrant.
Creiamo una directory per il progetto:
```
mkdir ubuntu-vms
cd ubuntu-vms
```
Adesso creiamo il Vagrantfile
```
vagrant init
//genera un Vagrant file di default
```
una classica configurazione per un file Vagrant puo\` essere la seguente:
```
# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
#
# Configurazione base per tutte le macchine
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end

  config.vm.define "vm1" do |vm1|
    vm1.vm.hostname = "c1-cp1"
    vm1.vm.network "private_network", ip: "192.168.56.11"
    vm1.vm.disk :disk, size: "50GB", name: "storage-1"
    vm1.vm.provider "virtualbox" do |vb|
      vb.name = "c1-cp1"
  end
end
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Disable the default share of the current code directory. Doing this
  # provides improved isolation between the vagrant box and your host
  # by making sure your Vagrantfile isn't accessible to the vagrant box.
  # If you use this you may want to enable additional shared subfolders as
  # shown above.
  # config.vm.synced_folder ".", "/vagrant", disabled: true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #  # Display the VirtualBox GUI when booting the machine
  #  vb.gui = true
  #
  #  # Customize the amount of memory on the VM:
  #  vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #  apt-get update
  #  apt-get install -y apache2
  # SHELL
end
```

```
# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # Define first VM (Ubuntu)
  config.vm.define "vm1" do |vm1|
    vm1.vm.box = "ubuntu/focal64"
    vm1.vm.network "private_network", ip: "192.168.56.101"
    vm1.vm.hostname = "vm1"
  end

  #Define second VM (Ubuntu)
  config.vm.define "vm2" do |vm2|
    vm2.vm.box = "ubuntu/focal64"
    vm2.vm.network "private_network", ip: "192.168.56.102"
    vm2.vm.hostname = "vm2"
  end
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "base"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Disable the default share of the current code directory. Doing this
  # provides improved isolation between the vagrant box and your host
  # by making sure your Vagrantfile isn't accessible to the vagrant box.
  # If you use this you may want to enable additional shared subfolders as
  # shown above.
  # config.vm.synced_folder ".", "/vagrant", disabled: true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #  # Display the VirtualBox GUI when booting the machine
  #  vb.gui = true
  #
  #  # Customize the amount of memory on the VM:
  #  vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #  apt-get update
  #  apt-get install -y apache2
  # SHELL
end
```
Per startare le nostre VM:
```
vagrant up
// dall'interno della directory dove risiede il VagrantFile
```

Una volta che le due VM stanno runnando per loggare all' interno:
```
vagrant ssh <nome|id>
```
Se vogliamo collegarci alla seconda macchina virtuale mentre siamo nella prima:
Prima VM: vm1
Seconda VM: vm2
```
vagrant ssh vm1
```
per sicurezza controlliamo che openssh-server sia installato
```
sudo apt update
sudo apt upgrade
sudo apt install openssh-server
sudo systemctl status ssh
// controllare che sia running state
// fare lo stesso in vm2
```
Se e\` tutto ok procediamo nel creare una nuova Key:
```
vagrant ssh vm1
ssh-keygen -t rsa -b 2048 -f ~/.ssh/my_vagrant_key
//in .ssh avremo due nuovi file
//my_vagrant_key my_vagrant_key.pub

//cosi copiamo la chiave appena generata e la colleghiamo alla
// seconda vm
ssh-copy-id -i ~/.ssh/my_vagrant_key.pub vagrant@192.168.56.102
```
Then to access to our second vm:
```
ssh -i ~/.ssh/my_vagrant_key hostname@ip
```

# Debian Shortcut

|     |     |
| --- | --- |
| **Shortcut** | **Utility** |
| Ctrl+Alt+Delete | Use this shortcut to logout of Debian. |
| Alt+Tab/ Super+Tab | Use this shortcut to switch between open programs. |
| Ctrl+Alt+Tab | Use this shortcut to switch between system controls such as Windows, Top Bar, and Desktop. |
| Ctrl+Alt +Esc | Use this shortcut to directly switch between system controls. |
| Super+L | Use this shortcut to lock the screen. |
| Super+A | Use this shortcut to view all applications. |
| Super+V | Use this shortcut to view notifications, if any. |
| Super+S | Use this shortcut to get an overview of open activities. |
| Alt+F1 | Use this shortcut to get an overview of open windows. |
| Alt+F2 | Use this shortcut to open the Run command dialog. |
| Alt+F4 | Use this shortcut to close the current window. |
| Alt +F5 | Use this shortcut to unmaximize the current window. |
| Alt+F7 | Use this shortcut to select the current window for moving. |
| Alt+F8 | Use this shortcut to resize the current window. |
| Alt+F10 | Use this shortcut to minimize or maximize the current window. |
| Alt+Space | Use this shortcut to view the window menu used to maximize, minimize, move, close, etc. the current window. |
| Super+Pageup | Use this shortcut to move to the above workspace. |
| super+Pagedown | Use this shortcut to move to the below workspace. |
| Super+Home | Use this shortcut to move to the first workspace. |
| Super+End | Use this shortcut to move to the last workspace. |
| Shift+Super+Home | Use this shortcut to move the window to the first workspace. |
| Shift+Super+End | Use this shortcut to move the window to the last workspace. |
| Shift+Super+Up/Shift+<br><br>Super+Down | Use this shortcut to move the window up/down. |
| Shift+Super+Left/Shift+ Super+Right | Use this shortcut to move the window left/right. |
