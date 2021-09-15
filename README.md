antes que nada actualizamos los paquetes 
```
yum update
```
Instalar repositorio EPEL

```
yum install -y epel-release
dnf install langpacks-en glibc-all-langpacks -y
```
Instalar pre-requisitos de Ansible AWX:


centos 7
```
yum install -y git gcc gcc-c++ nodejs gettext device-mapper-persistent-data lvm2 bzip2 python-pip yum-utils ansible python3 libselinux-python3 python36-docker
```

centos8
```
yum install git gcc gcc-c++ nodejs gettext device-mapper-persistent-data lvm2 bzip2 platform-python-pip.noarch yum-utils ansible python3 libselinux-python3 python-docker-tests.noarch
```

Instalar Docker CE (Comunity Edition):
```
yum-config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
yum install -y docker-ce
systemctl enable --now docker.service
```
output
```
docker --version 
Docker version 20.10.8, build 3967b7d 
```

Instalar Docker-Compose
docker-compose en realidad lo que hace es administrar contenedores 


```
curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

output
``` 
docker-compose
docker-compose --version
```

Instalando Ansible AWX on CentOS 7:
```
cd /tmp
git clone https://github.com/intidelrio/ansible-tower.git
```

Definir un password para acceder al portal de AWX: 
```
cd ansible-tower/ansible-tower/awx-17.1.0/inventory

vim +108 inventory

admin_user=admin
admin_password=password

```

Instalando pip  docker
```
yum install python3-pip -y 
pip3 install -y docker-compose
yum install -y nodejs npm python3-pip git pwgen libselinux-python3 
pip3 install -y setuptools_rust 
pip3 install -y cryptography 
pip3 install -y wheel
pip3 install --upgrade pip
```

Luego ejecutar el playbook para la instalacion:
```
ansible-playbook -i inventory install.yml
```

por ultimo 
```
http://ip-del-servidor
```

