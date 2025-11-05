## Garantindo a mesma versão de Ansible para equipe

    python3 -m venv venv
    source venv/bin/activate
    ./venv/bin/pip3 install -r requirements.txt
    ./venv/bin/ansible --version

Assim vamos rodar o ansible sempre:

    ./venv/bin/ansible-galaxy install -r requirements.yml --force
    ./venv/bin/ansible-playbook playbooks/dev/drupal.yml



## Preparação do ambiente

Instale na sua distro: vagrant

Instalação e configuração do libvirt para criar virtualização:

    $ sudo apt install virt-manager libvirt-dev ansible
    $ sudo adduser SEU-USER libvirt

Instalação do plugin do libvirt no ansible:

    $ vagrant plugin install vagrant-libvirt

Instalação das roles do ansible

    git clone https://github.com/fflch/provisioner-dev.git
    cd provisioner-dev
    ansible-galaxy install -r requirements.yml --force
