Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.hostname = "unifi"
  config.vm.provider "virtualbox" do |v|
    v.name = "unifi"
  end

  config.vm.network "public_network",
    bridge: "en0: Ethernet"

  config.vm.network "forwarded_port",
    guest: 3478, host: 3478, protocol: "udp"
  config.vm.network "forwarded_port",
    guest: 8080, host: 8080
  config.vm.network "forwarded_port",
    guest: 8443, host: 8443
  config.vm.network "forwarded_port",
    guest: 6789, host: 6789
  config.vm.network "forwarded_port",
    guest: 10001, host: 10001, protocol: "udp"

  config.vm.provision :docker
  config.vm.provision "shell", inline: <<-SHELL
    cd /vagrant
    docker compose stop
    docker compose up -d
  SHELL
end
