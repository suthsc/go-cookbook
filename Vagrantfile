require 'berkshelf/vagrant'

box_name = "opscode_ubuntu-12.04_chef-11.2.0"
box_url  = "https://opscode-vm.s3.amazonaws.com/vagrant/#{box_name}.box"

Vagrant::Config.run do |config|
  config.vm.box = box_name
  config.vm.box_url = box_url

  config.vm.network :hostonly, "192.168.192.2"

  config.vm.provision :chef_solo do |chef|
    chef.json = {
      "go" => {
        "server" => "127.0.0.1",
        "auto_register_agents" => true,
        "auto_register_agents_key" => "batshit"
      }
    }

    chef.run_list = [
      "recipe[apt]", "recipe[go::server]","recipe[go::agent]"
    ]
  end
end
