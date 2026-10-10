Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.hostname = "unifi"
  config.vm.provider "virtualbox" do |v|
    v.name = "unifi"
  end

  config.vm.network "public_network",
    bridge: "en0: Ethernet"

  config.vm.synced_folder ".", "/vagrant", type: "nfs",
    nfs_udp: false
  # Required for nfs folder sharing
  config.vm.network "private_network", type: "dhcp"

  config.vm.provision :docker
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt install -y avahi-daemon
    cd /vagrant
    docker compose stop
    docker compose up -d --pull always --force-recreate
  SHELL
end
