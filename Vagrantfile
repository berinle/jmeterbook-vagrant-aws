Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.provider :aws do |aws, override|
    aws.access_key_id = "YOUR AWS KEY ID"
    aws.secret_access_key = "YOUR AWS SECRET KEY"
    aws.keypair_name = "YOUR KEYPAIR NAME"    
    aws.region = "YOUR AWS REGION"
    aws.ami = "ami-7747d01e"

    override.ssh.private_key_path = "PATH TO YOUR PRIVATE KEY"    
    override.ssh.username = "ubuntu"
  end

  # define multiple VMs.
  config.vm.define :vm1
  config.vm.define :vm2
  config.vm.define :vm3
  config.vm.define :vm4

  config.vm.synced_folder "testplans", "/home/ubuntu/testplans"

  # provision with shell
  config.vm.provision :shell,
    :inline => "apt-get update && apt-get -q -y install puppet"    

  # provision with puppet
  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "manifests"
    puppet.module_path = "modules"
    puppet.manifest_file  = "main.pp"
  end

end
