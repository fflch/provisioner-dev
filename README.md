## Preparação do ambiente (testado com debian 10/11)

Instale na sua distro: ansible, vagrant

Instalação e configuração do libvirt para criar virtualização:

    $ sudo apt install virt-manager libvirt-dev ansible
    $ sudo addgroup SEU-USER libvirt

Instalação do plugin do libvirt no ansible:

    $ vagrant plugin install vagrant-libvirt

Instalação das roles do ansible

    ansible-galaxy install -r requirements.yml
