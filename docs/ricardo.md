# Basta usar a imagem minio/minio:RELEASE.2025-04-22T22-12-26Z
# https://github.com/kevincoakley/ansible-role-disk
# https://github.com/tinslice/ansible-role-disks
<!-- - name: Criar filesystem XFS -->
<!--   community.general.filesystem: -->
<!--     fstype: xfs -->
<!--     dev: /dev/sdb -->
<!--     opts: "-i size=512 -n ftype=1 -L RUSTFS0" -->

https://www.min.io/product/erasure-code-calculator

vagrant up d13-miniofflch d13-miniofflchreplica

Ambas máquinas tem /dev/vdb e /dev/vdc

vagrant ssh d13-miniofflch
vagrant ssh d13-miniofflchreplica

Configurar discos:

apt update
apt install xfsprogs -y

fdisk /dev/vdb: n, p -> w
fdisk /dev/vdc

mkfs.xfs /dev/vdb1
mkfs.xfs /dev/vdc1

mkdir -p /data1
mkdir -p /data2

blkid

/dev/vdb1 UUID="1e471b63-938d-4172-964e-19fd01bb0e0b"
/dev/vdc1 UUID="382275d8-cae6-432f-8ea8-1c94e95ecedb"

/etc/fstab

UUID="1e471b63-938d-4172-964e-19fd01bb0e0b" /data1 xfs defaults,noatime 0 2
UUID="382275d8-cae6-432f-8ea8-1c94e95ecedb" /data2 xfs defaults,noatime 0 2

systemctl daemon-reload
mount -a

useradd -r minio -s /sbin/nologin

mkdir -p /data1/minio
mkdir -p /data2/minio

chown -R minio:minio /data1/minio
chown -R minio:minio /data2/minio


### Instalação nos 3

cd /usr/local/bin

wget https://dl.min.io/server/minio/release/linux-amd64/minio
chmod +x minio

wget https://dl.min.io/client/mc/release/linux-amd64/mc
chmod +x mc


#### /etc/systemd/system/minio.service

[Unit]
Description=MinIO
After=network.target

[Service]
User=minio
Group=minio

Environment="MINIO_ROOT_USER=admin"
Environment="MINIO_ROOT_PASSWORD=SenhaMuitoForte"

ExecStart=/usr/local/bin/minio server \
    /data1/minio \
    /data2/minio \
    --console-address ":9001"

Restart=always
LimitNOFILE=65536

[Install]
WantedBy=multi-user.target


### serviços
systemctl daemon-reload
systemctl enable --now minio


http://192.168.8.100:9001/login


No miniofflch:

mc alias set miniofflch http://192.168.8.100:9000  admin SenhaMuitoForte
mc alias set miniofflchreplica http://192.168.8.101:9000  admin SenhaMuitoForte


mc admin replicate add miniofflch miniofflchreplica

Criar Bucket:

mc mb miniofflch/chamado.fflch.usp.br
mc version enable miniofflch/chamado.fflch.usp.br

#### playbook deve ser capaz de:

- Adicionar novos discos - basta preparar os disco e alterar  /etc/systemd/system/minio.service e systemctl daemon-reload systemctl restart minio
- Nã implementar remoção de discos




