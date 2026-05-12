https://www.min.io/product/erasure-code-calculator

vagrant up d13-minio1 d13-minio2 d13-minio3 d13-minio4 d13-miniobackup

Todas máquinas tem /dev/vdb e /dev/vdc

vagrant ssh d13-minio1
vagrant ssh d13-minio2
vagrant ssh d13-minio3
vagrant ssh d13-minio4
vagrant ssh d13-miniobackup

cat >> /etc/hosts <<EOF
192.168.8.100 miniobackup
192.168.8.101 minio1
192.168.8.102 minio2
192.168.8.103 minio3
192.168.8.104 minio4
EOF

mkdir -p /data/minio
mkdir -p /etc/minio

useradd -r minio -s /sbin/nologin
chown -R minio:minio /data/minio


### Instalação nos 3

cd /usr/local/bin
wget https://dl.min.io/server/minio/release/linux-amd64/minio
chmod +x minio

wget https://dl.min.io/client/mc/release/linux-amd64/mc
chmod +x mc
mv mc /usr/local/bin/


#### /etc/default/minio

MINIO_ROOT_USER=admin
MINIO_ROOT_PASSWORD=SenhaMuitoForte

MINIO_VOLUMES="http://minio1/data/minio \
http://minio2/data/minio \
http://minio3/data/minio \
http://minio4/data/minio"

MINIO_OPTS="--console-address :9001"

#### permissões
chown minio:minio /etc/default/minio
chmod 640 /etc/default/minio

#### /etc/systemd/system/minio.service

[Unit]
Description=MinIO Distributed
Documentation=https://min.io
After=network-online.target
Wants=network-online.target

[Service]
User=minio
Group=minio

EnvironmentFile=/etc/default/minio

ExecStart=/usr/local/bin/minio server $MINIO_VOLUMES $MINIO_OPTS

Restart=always
LimitNOFILE=65536
TasksMax=infinity
TimeoutStopSec=infinity

[Install]
WantedBy=multi-user.target


### serviços 
systemctl daemon-reload
systemctl enable minio
systemctl start minio



http://192.168.8.100:9001/login


No minio1: 

mc alias set minio1 http://192.168.8.100:9000 admin SenhaMuitoForte
mc alias set minio2 http://192.168.8.101:9000 admin SenhaMuitoForte
mc alias set miniobackup http://192.168.8.102:9000 admin SenhaMuitoForte

mc admin info minio1
mc admin info minio2
mc admin info miniobackup

mc admin replicate add minio1 minio2

Criar Bucket:

mc mb minio1/chamado.fflch.usp.br
mc version enable minio1/chamado.fflch.usp.br


d13-miniobackup - deixaremos para o zé fazer o script de backup


