wiki:

    https://github.com/GCRC/nunaliit_tutorial/wiki

Passos para instalação do nunaliit:

    sudo apt install -y openjdk-8-jre-headless apt-transport-https curl gnupg

Repositório para couchdb:

    curl https://couchdb.apache.org/repo/keys.asc | /usr/bin/gpg --dearmor | /usr/bin/tee /usr/share/keyrings/couchdb-archive-keyring.gpg >/dev/null 2>&1

    echo "deb [signed-by=/usr/share/keyrings/couchdb-archive-keyring.gpg] https://apache.jfrog.io/artifactory/couchdb-deb/ bionic main" | sudo tee /etc/apt/sources.list.d/couchdb.list >/dev/null

Instalação do couchdb como standalone e bind address '0.0.0.0', crie uma senha e guarde-a:

    apt update
    apt install -y couchdb=2.3.1~bionic
    apt-mark hold couchdb
    systemctl restart couchdb

Mais pacotes:

    sudo apt install -y imagemagick ffmpeg ubuntu-restricted-extras

Site para Download:

    https://github.com/GCRC/nunaliit/releases

Downlaod:

    wget https://github.com/GCRC/nunaliit/releases/download/2.2.9-SNAPSHOT/nunaliit_2.2.9-SNAPSHOT_2022-04-12_a34e51b.zip
    unzip nunaliit_2.2.9-SNAPSHOT_2022-04-12_a34e51b.zip
    ./nunaliit_2.2.9-SNAPSHOT_2022-04-12_a34e51b/bin/nunaliit create

Respostas:

    Enter location where atlas should be created: atlasthiago
    Enter the name of the atlas [atlasthiago]: 
    Enter the URL to CouchDB [http://127.0.0.1:5984/]: 
    Enter the name of the main database where atlas resides [atlasthiago]: 
    Do you wish to manually verify each document submission?(Y/N) [N]: 
    Enter the name of the admin user for CouchDB [admin]: 
    Enter the password for the admin user [admin_password]: admin
    Enter the port where the atlas is served [8080]: 
    Enter a Google Map API key (empty if not using):

Migrate database e levantando serviço:

    cd atlasthiago/
    ../nunaliit_2.2.9-SNAPSHOT_2022-04-12_a34e51b/bin/nunaliit update
    ../nunaliit_2.2.9-SNAPSHOT_2022-04-12_a34e51b/bin/nunaliit run

couchdb na máquina virtual:

    http://192.168.8.57:5984/atlasthiago

Atlas:

    http://192.168.8.57:8080/


Colocar informações no Bloco da direita: 

    module.demo/nunaliit_module/introduction/content/en.html

Perguntas:

    - se a lógica do nunaliit preve que alteramos os arquivos das pastas docs e htdosc, como é feita a atualização do projeto?
    - how to keep service up
    - how to configure PATH do exposer nunaliit/bin system wide
    - cenário multi-user como funciona, dado que o nunaliit tem vários função via cli?