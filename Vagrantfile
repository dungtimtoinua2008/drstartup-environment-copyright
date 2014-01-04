# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"


Vagrant::Config.run do |config|
  config.vm.forward_port 80, 8080
end

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "drstartup"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

config.vm.provision :chef_solo do |chef|
   chef.cookbooks_path = "chef/cookbooks"
   #chef.roles_path = "../my-recipes/roles"
   #chef.data_bags_path = "../my-recipes/data_bags"
   chef.add_recipe "xcode"
   chef.log_level = :debug
   #chef.add_role "web"

   # You may also specify custom JSON attributes:
   chef.json = { 
       "mysql" => {
           "server_root_password" => "abc123"
           },

       "nginx" => {
           "root_dir" => "/vagrant/webapp"
       }
   }

end

end