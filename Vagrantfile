# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'

Vagrant.require_version '>= 1.5.0'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  ##config.vm.hostname = 'oel7multinode1-berkshelf'

  # Set the version of chef to install using the vagrant-omnibus plugin
  # NOTE: You will need to install the vagrant-omnibus plugin:
  #
  #   $ vagrant plugin install vagrant-omnibus
  #
  ##if Vagrant.has_plugin?("vagrant-omnibus")
  ##  config.omnibus.chef_version = 'latest'
  ##end

  # Every Vagrant virtual environment requires a box to build off of.
  # If this value is a shorthand to a box in Vagrant Cloud then
  # config.vm.box_url doesn't need to be specified.
  #config.vm.box = 'chef/ubuntu-14.04'
  config.vm.box = 'oel72-64-model'
  config.ssh.password = 'vagrant'
  config.vm.synced_folder  "../../stage/Oracle12c/grid", "/stage-grid"
  config.vm.synced_folder  "../../stage/Oracle12c/database", "/stage-database"

  config.vm.provider "virtualbox" do |vb|  # common for all nodes
    vb.memory = 6144
    vb.cpus = 1
  end # common for all nodes

#--------------NODE1-------------
  config.vm.define "rac1n1" do |node|  # node1
    node.vm.hostname = "rac1n1"
    node.vm.network "private_network", ip: "192.168.0.111", virtualbox__intnet: true  # public
    node.vm.network "private_network", ip: "10.10.10.111", virtualbox__intnet: true   # private interconnect

    config.vm.provider "virtualbox" do |vb|  # node1 customize

      # Disk 1
      file_name='C:\VMDisks\cbora12crac1rs\asm1.vmdk'
      file_type='vmdk'
      port_number=1
      if !File.exist?(file_name)
        puts ("creating file1")
        vb.customize ['createhd', '--variant', 'Fixed', '--filename', file_name, '--format', file_type, '--size', 2 * 1024]
        vb.customize ['modifyhd', file_name , '--type', 'shareable']
      end
      vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

      # Disk 2
      file_name='C:\VMDisks\cbora12crac1rs\asm2.vmdk'
      file_type='vmdk'
      port_number=2
      if !File.exist?(file_name)
        puts ("creating file2")
        vb.customize ['createhd', '--variant', 'Fixed', '--filename', file_name, '--format', file_type, '--size', 2 * 1024]
        vb.customize ['modifyhd', file_name , '--type', 'shareable']
      end
      vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

      # Disk 3
      file_name='C:\VMDisks\cbora12crac1rs\asm3.vmdk'
      file_type='vmdk'
      port_number=3
      if !File.exist?(file_name)
        puts ("creating file3")
        vb.customize ['createhd', '--variant', 'Fixed', '--filename', file_name, '--format', file_type, '--size', 2 * 1024]
        vb.customize ['modifyhd', file_name , '--type', 'shareable']
      end
      vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

      # Disk 4
      file_name='C:\VMDisks\cbora12crac1rs\asm4.vmdk'
      file_type='vmdk'
      port_number=4
      if !File.exist?(file_name)
        puts ("creating file4")
        vb.customize ['createhd', '--variant', 'Fixed', '--filename', file_name, '--format', file_type, '--size', 2 * 1024]
        vb.customize ['modifyhd', file_name , '--type', 'shareable']
      end
      vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]


      # Disk 5
      file_name='C:\VMDisks\cbora12crac1rs\asm5.vmdk'
      file_type='vmdk'
      port_number=5
      if !File.exist?(file_name)
        puts ("creating file5")
        vb.customize ['createhd', '--variant', 'Fixed', '--filename', file_name, '--format', file_type, '--size', 2 * 1024]
        vb.customize ['modifyhd', file_name , '--type', 'shareable']
      end
      vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

      # Disk 6
      file_name='C:\VMDisks\cbora12crac1rs\asm6.vmdk'
      file_type='vmdk'
      port_number=6
      if !File.exist?(file_name)
        puts ("creating file6")
        vb.customize ['createhd', '--variant', 'Fixed', '--filename', file_name, '--format', file_type, '--size', 2 * 1024]
        vb.customize ['modifyhd', file_name , '--type', 'shareable']
      end
      vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

    end # node1 customize disk

    #Node1 provisioning
    # Shell provisioner
    node.vm.provision :shell, inline: 'echo rac1n1 shell provisioner working... echo'

    # Chef provisioner
    #node.omnibus.chef_version = '12.6.0'

    node.vm.provision :chef_solo do |chef|
      chef.run_list = [
      #'recipe[cbora12crac1rs::default]'
      #'recipe[cbora12crac1rs::default]','recipe[cbora12crac1rs::setup_ssh]','recipe[cbora12crac1rs::users_and_groups]', 'recipe[cbora12crac1rs::directories]','recipe[cbora12crac1rs::update_etc_hosts]','recipe[cbora12crac1rs::configure_oracleasm]','recipe[cbora12crac1rs::prepare_asm_disks]'
      #'recipe[cbora12crac1rs::users_and_groups]'
      #'recipe[cbora12crac1rs::update_etc_hosts]'
      #'recipe[cbora12crac1rs::install_sshpass]'
      #'recipe[cbora12crac1rs::setup_ssh]'
      #'recipe[cbora12crac1rs::directories]'
      #'recipe[cbora12crac1rs::configure_oracleasm]'
      'recipe[cbora12crac1rs::prepare_asm_disks]'
      ]
    end
  end # rac1n1 main

#--------------NODE2-------------
  config.vm.define "rac1n2" do |node| # node2
    node.vm.hostname = "rac1n2"
    node.vm.network "private_network", ip: "192.168.0.112", virtualbox__intnet: true  # public
    node.vm.network "private_network", ip: "10.10.10.112", virtualbox__intnet: true   # private interconnect

        config.vm.provider "virtualbox" do |vb|  # node2 customize

          # Disk 1
          file_name='C:\VMDisks\cbora12crac1rs\asm1.vmdk'
          file_type='vmdk'
          port_number=1
          vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

          # Disk 2
          file_name='C:\VMDisks\cbora12crac1rs\asm2.vmdk'
          file_type='vmdk'
          port_number=2
          vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

          # Disk 3
          file_name='C:\VMDisks\cbora12crac1rs\asm3.vmdk'
          file_type='vmdk'
          port_number=3
          vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

          # Disk 4
          file_name='C:\VMDisks\cbora12crac1rs\asm4.vmdk'
          file_type='vmdk'
          port_number=4
          vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

          # Disk 5
          file_name='C:\VMDisks\cbora12crac1rs\asm5.vmdk'
          file_type='vmdk'
          port_number=5
          vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

          # Disk 6
          file_name='C:\VMDisks\cbora12crac1rs\asm6.vmdk'
          file_type='vmdk'
          port_number=6
          vb.customize ["storageattach", :id, "--storagectl", "SATA", "--port", port_number, "--device", 0, "--type", "hdd", '--medium', file_name]

        end # node2 customize disk

        #Node2 provisioning
        # Provisioning steps

        # Shell provisioner
        node.vm.provision :shell, inline: 'echo rac1n2 shell provisioner working... echo'

        # Chef provisioner
        #node.omnibus.chef_version = '12.6.0'

        node.vm.provision :chef_solo do |chef|
          chef.run_list = [
          #'recipe[cbora12crac1rs::default]'
          #'recipe[cbora12crac1rs::users_and_groups]'
          #'recipe[cbora12crac1rs::update_etc_hosts]'
          #'recipe[cbora12crac1rs::install_sshpass]'
          #'recipe[cbora12crac1rs::setup_ssh]'
          #'recipe[cbora12crac1rs::directories]'
          ]
        end
  end # rac1n2 main

  # Assign this VM to a host-only network IP, allowing you to access it
  # via the IP. Host-only networks can talk to the host machine as well as
  # any other machines on the same network, but cannot be accessed (through this
  # network interface) by any external networks.
  #config.vm.network :private_network, type: 'dhcp'

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.


  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider :virtualbox do |vb|
  #   # Don't boot with headless mode
  #   vb.gui = true
  #
  #   # Use VBoxManage to customize the VM. For example to change memory:
  #   vb.customize ["modifyvm", :id, "--memory", "1024"]
  # end
  #
  # View the documentation for the provider you're using for more
  # information on available options.

  # The path to the Berksfile to use with Vagrant Berkshelf
  # config.berkshelf.berksfile_path = "./Berksfile"

  # Enabling the Berkshelf plugin. To enable this globally, add this configuration
  # option to your ~/.vagrant.d/Vagrantfile file
  config.berkshelf.enabled = true

  # An array of symbols representing groups of cookbook described in the Vagrantfile
  # to exclusively install and copy to Vagrant's shelf.
  # config.berkshelf.only = []

  # An array of symbols representing groups of cookbook described in the Vagrantfile
  # to skip installing and copying to Vagrant's shelf.
  # config.berkshelf.except = []


  ##config.vm.provision :chef_solo do |chef|
    ##chef.json = {
      ##mysql: {
        ##server_root_password: 'rootpass',
        ##server_debian_password: 'debpass',
        ##server_repl_password: 'replpass'
      ##}
    ##}

    ##chef.run_list = [

      ##'recipe[oel7multinode1::default]'
    ##]
  ##end

end
