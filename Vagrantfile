Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "256"
    vb.linked_clone = true
  end

  # Actualizar SO
  config.vm.provision "update", type: "shell", inline: <<-SHELL
    apt-get update 
  SHELL

  config.vm.define "atlas" do |atlas|
    atlas.vm.hostname = "atlas"  # Asignamos el nombre de host
    atlas.vm.network "private_network", ip: "192.168.56.10"  # IP fija

    atlas.vm.provision "bind9-install", type: "shell", inline: <<-SHELL
        apt-get install -y bind9 bind9-utils bind9-doc
    SHELL
  end

  config.vm.define "ceo" do |ceo|
    ceo.vm.hostname = "ceo"  # Asignamos el nombre de host
    ceo.vm.network "private_network", ip: "192.168.56.11"  # IP fija

    ceo.vm.provision "bind9-install", type: "shell", inline: <<-SHELL
        apt-get install -y bind9 bind9-utils bind9-doc
    SHELL
  end
end