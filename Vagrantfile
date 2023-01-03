VAGRANTFILE_API_VERSION = "2"
#ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  ### global configs
  config.ssh.insert_key = false # important

  config.vm.define "cups" do |host|
    host.vm.hostname = "cups"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.43",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 256
      v.cpus = 1
    end
  end

  config.vm.define "aegir" do |host| 
    host.vm.hostname = "aegir"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.44",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 2048
      v.cpus = 1
    end
  end

  config.vm.define "mariadbmaster" do |host|
    host.vm.hostname = "mariadbmaster"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.10",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 4024
      v.cpus = 1
    end
  end

  config.vm.define "nunaliit" do |host|
    host.vm.hostname = "nunaliit"
    host.vm.box = "generic/ubuntu1804"
    host.vm.network :private_network,
      :ip => "192.168.8.57",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 4096
      v.cpus = 4
    end
  end

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

  ### VMs
  config.vm.define "rsyslog" do |host|
    host.vm.hostname = "log"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.2",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 512
      v.cpus = 1
    end
  end

  config.vm.define "dhcp" do |host|
    host.vm.hostname = "dhcp"
    host.vm.box = "generic/ubuntu1604"
    host.vm.network :private_network,
      :ip => "192.168.8.40",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"

    host.vm.provider :libvirt do |v|
      v.memory = 256
      v.cpus = 1

    end
  end

  config.vm.define "freeradius" do |host|
    host.vm.hostname = "freeradius"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.41",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 512
      v.cpus = 1
    end
  end

  config.vm.define "projetos" do |host| 
    host.vm.hostname = "projetos"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.45",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 4024
      v.cpus = 1
    end
  end

  config.vm.define "firstdc" do |host|

    host.vm.hostname = "firstdc"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.48",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

  config.vm.define "anotherdc1" do |host|
    host.vm.hostname = "anotherdc1"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.49",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 384
      v.cpus = 1
    end
  end

  config.vm.define "anotherdc2" do |host|
    host.vm.hostname = "anotherdc2"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.50",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 384
      v.cpus = 1
    end
  end

  config.vm.define "replicado" do |host|
    host.vm.hostname = "replicado"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.56",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 4096
      v.cpus = 1
    end
  end

  config.vm.define "bind" do |host|
    host.vm.hostname = "bind"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.58",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

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

  config.vm.define "zoneminder" do |host|
    host.vm.hostname = "zoneminder"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.60",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 512
      v.cpus = 1
    end
    host.vm.network "forwarded_port", guest: 80, host: 46080
    host.vm.network "forwarded_port", guest: 22, host: 46022
  end

  config.vm.define "ftp" do |host|
    host.vm.hostname = "ftp"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.61",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 512
      v.cpus = 1
    end
  end

  config.vm.define "nginxrevproxy" do |host|
    host.vm.hostname = "nginxrevproxy"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.62",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 512
      v.cpus = 1
    end
  end

  config.vm.define "f-secure" do |host|
    host.vm.hostname = "f-secure"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.90",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 384
      v.cpus = 1
    end
  end

  config.vm.define "phpserver" do |host|
    host.vm.hostname = "phpserver"
    host.vm.box = "generic/debian10"
    host.vm.network :private_network,
      :ip => "192.168.8.92",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 512
      v.cpus = 1
    end
  end

  config.vm.define "aegirmigrate" do |host| 
    host.vm.hostname = "aegirmigrate"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.93",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 1024
      v.cpus = 1
    end
  end

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

  config.vm.define "proaluno" do |host| 
    host.vm.hostname = "proaluno"
    host.vm.box = "generic/debian10"
    #host.vm.box_version = "3.0.36"
    host.vm.network :private_network,
      :ip => "192.168.8.47",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 4096
      v.cpus = 1
    end
  end

  config.vm.define "printers" do |host| 
    host.vm.hostname = "printers"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.53",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 2048
      v.cpus = 1
    end
  end

  config.vm.define "rshiny" do |host|
    host.vm.hostname = "rshiny"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.3",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 256
      v.cpus = 1
    end
  end

  config.vm.define "postgresql" do |host|
    host.vm.hostname = "postgresql"
    host.vm.box = "generic/debian11"
    host.vm.network :private_network,
      :ip => "192.168.8.4",
      :libvirt__network_name => "fflch",
      :libvirt__forward_mode => "nat"
    host.vm.provider :libvirt do |v|
      v.memory = 256
      v.cpus = 1
    end
  end

end
