# Basic configuration to run Vagrant on Windows
Vagrant.configure(2) do |config|
  config.vm.box = "bento/ubuntu-16.04" # Box with Ubuntu 16.04 LTS
  config.vm.provider "virtualbox" do |vb| # VirtualBox provider
     vb.name = "vagrant_pc" # Name of the Virtual Machine, you can select yours
     vb.memory = 2048 # Ram memory for virtual machine
     vb.cpus = 2 # Number of CPU's for virtual machine
  end
  config.vm.network "forwarded_port", guest: 80, host: 8080 # Forwarding the port for serving websites
  config.vm.network :private_network, ip: "192.168.20.13" # Assigning ip address to connect through putty
  config.vm.synced_folder "../../sites", "/var/www", type: "smb",
    owner: 'vagrant', group: 'www-data',
    mount_options: ["dir_mode=0775,file_mode=0776"] # Synced folders using SMB (only for Windows)
  config.vm.synced_folder "../../scripts", "/home/vagrant/bin", type: "smb" # You can add any synced folder that you want
  config.vm.hostname = 'cydetec.dev' # Hostname for Vagrant Host Manager
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.include_offline = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.aliases = %w(other.dev other2.dev) # Alternative hostnames. Each hostname can have a config file in nginx
end
