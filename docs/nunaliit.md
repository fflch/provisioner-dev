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

Criando esquema para restaurante:

    ../nunaliit_2.2.9-SNAPSHOT_2022-04-12_a34e51b/bin/nunaliit add-schema --id restaurante
    ls docs/schema.atlasthiago_restaurante/

cat docs/schema.atlasthiago_restaurante/definition.json

    {
        "id": "restaurante",
        "group": "atlasthiago"
    }

Novo conteúdo de docs/schema.atlasthiago_restaurante/definition.json:

    {
        "group": "atlasthiago"
        ,"id": "restaurante"
        ,"label": "Restaurantes"
        ,"relatedSchemas": [ ]
        ,"initialLayers": [ "public" ]
        ,"attributes":[
        {
            "type":"string"
            ,"id":"name"
            ,"label":"Name"
            ,"includedInBrief":true
        }
        ,{
            "type":"string"
            ,"id":"address"
            ,"label":"Address"
            ,"textarea": true
        }
        ,{
            "type":"string"
            ,"id":"phone_number"
            ,"label":"Phone #"
        }
        ]
    }

Carregando novo schema:

    ../nunaliit_2.2.9-SNAPSHOT_2022-04-12_a34e51b/bin/nunaliit update-schema --name atlasthiago_restaurante
    ../nunaliit_2.2.9-SNAPSHOT_2022-04-12_a34e51b/bin/nunaliit update

Criando módulo:

    cd docs
    cp -a module.demo/ module.thiago_map
    echo 'module.thiago_map' > module.thiago_map/_id.txt

Alterando título do módulo:

    module.thiago_map/nunaliit_module/title.json

Adicionando formato tiled em module.thiago_map/nunaliit_module/display.json:

    {
        "defaultSchemaName":"demo_doc",
        "type":"tiled"
    }

URL do novo módulo:

    http://192.168.8.57:8080/index.html?module=module.thiago_map

Longitude e latitude para usp (module.thiago_map/nunaliit_module/map.json):

    "initialBounds": [-46.73,-23.57,-46.71,-23.55]

Habilitando bolinha do mouse (module.thiago_map/nunaliit_module/map.json):

    ,"toggleClick": true
    ,"enableWheelZoom": true

Deixando o módulo as default:

    config.directory.customService.setOption('defaultModuleIdentifier','module.thiago_map');
    or: customService.setOption('defaultModuleIdentifier','module.thiago_map');

Criando o idioma português em htdocs/nunaliit_custom.js

    window.nunaliit_custom.configuration = function(config, callback){
            var ptDef = {
                code: 'pt_br',
                name: 'Português'
            };
            config.directory.languageService.addLanguage(ptDef);

Carregando novos js. Em htdocs/nunaliit_custom.js, exatamente antes de `})(jQuery,nunaliit2);`:

    $n2.scripts.loadCustomScripts([
        'js/thiago.js'
    ]);

Criando um novo menu a partir de navigation.demo:

    cp -a docs/navigation.demo/ docs/navigation.menuthiago
    echo 'navigation.menuthiago' > docs/navigation.menuthiago/_id.txt

Links no docs/navigation.menuthiago/nunaliit_navigation.json:

    {
        "nunaliit_type":"navigation"
        ,"title":{
            "nunaliit_type":"localized"
            ,"en":"Atlas do thiago"
        }
        ,"items":[
            {
                "title": {
                    "nunaliit_type":"localized"
                    ,"en":"Módulo Demo"
                }
                ,"module": "module.demo"
            }
            ,{
                "title": {
                    "nunaliit_type":"localized"
                    ,"en":"Módulo Thiago"
                }
                ,"module": "module.thiago_map"
                ,"items":[
                    {
                        "title": {
                            "nunaliit_type":"localized"
                            ,"en":"Descrição do módulo do Thiago"
                        }
                        ,"href": "./thiago.html"
                    }
                ]
            }
        ]
    }

Mudar menu default htdocs/nunaliit_custom.js:

    customService.setOption('defaultNavigationIdentifier','navigation.menuthiago');

Partes que pulei:
    
    - wiki fiz, mas não funcionou
    - reference field js function
    - set defaul modulo is not working (htdocs/nunaliit_custom.js)

Perguntas:

    - se a lógica do nunaliit preve que alteramos os arquivos das pastas docs e htdosc, como é feita a atualização do projeto?
    - uma instancia do nunallit para cada projeto?
    - how to keep service up
    - how to configure PATH do exposer nunaliit/bin system wide
    - cenário multi-user como funciona, dado que o nunaliit tem vários função via cli?
    - why apt-mark hold couchdb?
    - schema managment whats is better? IDE oy definition.json