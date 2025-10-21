VAGRANTFILE_API_VERSION = "2"
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  ### global configs
  config.ssh.insert_key = false # important

  # 192.168.8.2
  config.vm.define "rsyslog" do |host|
    host.vm.hostname = "log"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.2",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.3
  config.vm.define "rshiny" do |host|
    host.vm.hostname = "rshiny"
    host.vm.box = "generic/debian12"
    host.vm.network :private_network,
      :ip => "192.168.8.3",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.4
  config.vm.define "postgresql" do |host|
    host.vm.hostname = "postgresql"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.4",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.5
  config.vm.define "ocsinventoryserver" do |host|
    host.vm.hostname = "ocsinventoryserver"
    host.vm.box = "generic/debian12"
    host.vm.network :private_network,
      :ip => "192.168.8.5",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.6 livre
  # 192.168.8.7 livre
  # 192.168.8.8 livre
  # 192.168.8.9 livre

  # 192.168.8.10
  # Na produção está debian 10, mas aqui coloquei debian 13 porque a VM não roda apt update, dado que o debian 10 não tem mais suporte
  # mudando para  cloud-image/debian-13 pois a Generic não tem suporte para debian 13 ainda
  config.vm.define "mariadbserver" do |host|
    host.vm.hostname = "mariadbserver"
    host.vm.box = "generic/debian12"
    host.vm.network :private_network,
      :ip => "192.168.8.10",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.11
  config.vm.define "django" do |host|
    host.vm.hostname = "django"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.11",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.12 livre
  # 192.168.8.13 livre
  # 192.168.8.14 livre
  # 192.168.8.15 livre
  # 192.168.8.16 livre
  # 192.168.8.17 livre
  # 192.168.8.18 livre
  # 192.168.8.19 livre
  # 192.168.8.20 livre
  # 192.168.8.21 livre
  # 192.168.8.22 livre
  # 192.168.8.23 livre
  # 192.168.8.24 livre
  # 192.168.8.25 livre
  # 192.168.8.26 livre
  # 192.168.8.27 livre
  # 192.168.8.28 livre
  # 192.168.8.29 livre
  # 192.168.8.30 livre
  # 192.168.8.31 livre
  # 192.168.8.32 livre
  # 192.168.8.33 livre
  # 192.168.8.34 livre
  # 192.168.8.35 livre
  # 192.168.8.36 livre
  # 192.168.8.37 livre
  # 192.168.8.38 livre
  # 192.168.8.39 livre

  # 192.168.8.40
  # Foi usado debian/bookworm64 e não generic/debian12 porque no generic/debian12
  # ipv6 não está habilitado por padrão
  config.vm.define "dhcp" do |host|
    host.vm.hostname = "dhcp"
    host.vm.box = "debian/bookworm64"
    host.vm.network :private_network,
      :ip => "192.168.8.40",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provision "shell",
      run: "always",
      inline: "ip -6 addr add 2001:0db8:cafe:40::10 dev eth1"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1

    end
  end

  # 192.168.8.41
  config.vm.define "freeradius" do |host|
    host.vm.hostname = "freeradius"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.41",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.42 livre

  # 192.168.8.43
  config.vm.define "cups" do |host|
    host.vm.hostname = "cups"
    host.vm.box = "generic/debian12"
    host.vm.network :private_network,
      :ip => "192.168.8.43",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.44
  config.vm.define "drupal" do |host|
    host.vm.hostname = "drupal"
    host.vm.box = "generic/debian12"
    host.vm.network :private_network,
      :ip => "192.168.8.44",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 2048
      v.cpus = 1
    end
  end

  # 192.168.8.45 livre

  # 192.168.8.46
  config.vm.define "boa" do |host|
    host.vm.hostname = "boa"
    host.vm.box = "generic-x64/devuan5"
    host.vm.network :private_network,
      :ip => "192.168.8.46",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 4096
      v.cpus = 2
    end
  end

  # 192.168.8.47
  config.vm.define "proaluno" do |host|
    host.vm.hostname = "proaluno"
    host.vm.box = "generic/debian12"
    host.vm.network :private_network,
      :ip => "192.168.8.47",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 2048
      v.cpus = 2
    end
  end

  # 192.168.8.48
  config.vm.define "firstdc" do |host|
    host.vm.hostname = "firstdc"
    host.vm.box = "generic/debian12"
    host.vm.network :private_network,
      :ip => "192.168.8.48",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.49
  config.vm.define "anotherdc1" do |host|
    host.vm.hostname = "anotherdc1"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.49",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.50
  config.vm.define "anotherdc2" do |host|
    host.vm.hostname = "anotherdc2"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.50",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.51 livre
  # 192.168.8.52 livre

  # 192.168.8.53
  config.vm.define "printers" do |host|
    host.vm.hostname = "printers"
    host.vm.box = "generic/debian12"
    host.vm.network :private_network,
      :ip => "192.168.8.53",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 2048
      v.cpus = 1
    end
  end

  # 192.168.8.54 livre
  # 192.168.8.55 livre

  # 192.168.8.56
  config.vm.define "replicado" do |host|
    host.vm.hostname = "replicado"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.56",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 2048
      v.cpus = 1
    end
  end

  # 192.168.8.57
  config.vm.define "nunaliit" do |host|
    host.vm.hostname = "nunaliit"
    host.vm.box = "generic/ubuntu1804"
    host.vm.network :private_network,
      :ip => "192.168.8.57",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 2048
      v.cpus = 4
    end
  end

  # 192.168.8.58
  config.vm.define "bind" do |host|
    host.vm.hostname = "bind"
    host.vm.box = "debian/bookworm64"
    host.vm.network :private_network,
      :ip => "192.168.8.58",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.59
  config.vm.define "entrypointbackup" do |host|
    host.vm.hostname = "entrypointbackup"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.59",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.60
  config.vm.define "zoneminder" do |host|
    host.vm.hostname = "zoneminder"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.60",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
    host.vm.network "forwarded_port", guest: 80, host: 46080
    host.vm.network "forwarded_port", guest: 22, host: 46022
  end

  # 192.168.8.61
  config.vm.define "ftp" do |host|
    host.vm.hostname = "ftp"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.61",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.62
  config.vm.define "nginxrevproxy" do |host|
    host.vm.hostname = "nginxrevproxy"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.62",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.63 livre
  # 192.168.8.64 livre
  # 192.168.8.65 livre
  # 192.168.8.66 livre
  # 192.168.8.67 livre
  # 192.168.8.68 livre
  # 192.168.8.69 livre
  # 192.168.8.70 livre
  # 192.168.8.71 livre
  # 192.168.8.72 livre
  # 192.168.8.73 livre
  # 192.168.8.74 livre
  # 192.168.8.75 livre
  # 192.168.8.76 livre
  # 192.168.8.77 livre
  # 192.168.8.78 livre
  # 192.168.8.79 livre
  # 192.168.8.80 livre
  # 192.168.8.81 livre
  # 192.168.8.82 livre
  # 192.168.8.83 livre
  # 192.168.8.84 livre
  # 192.168.8.85 livre
  # 192.168.8.86 livre
  # 192.168.8.87 livre
  # 192.168.8.88 livre
  # 192.168.8.89 livre

  # 192.168.8.90
  config.vm.define "fsecure" do |host|
    host.vm.hostname = "fsecure"
    host.vm.box = "debian/bookworm64"
    host.vm.network :private_network,
      :ip => "192.168.8.90",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.91 livre

  # 192.168.8.92
  config.vm.define "php8server" do |host|
    host.vm.hostname = "php8server"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.92",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  # 192.168.8.93

  # 192.168.8.94
  config.vm.define "hpc" do |host|
    host.vm.hostname = "hpc"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.94",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 2048
      v.cpus = 2
    end
  end

  # 192.168.8.95 livre
  # 192.168.8.96 livre
  # 192.168.8.97 livre
  # 192.168.8.98 livre
  # 192.168.8.99 livre
  # 192.168.8.100 livre
end
