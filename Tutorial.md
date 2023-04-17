Adicionando o openvpn-2.5.5 ao fedora 37 e 38


1- Entre em modo root:

su

2- Instale os seguintes pacotes:

dnf install lzo-devel pam-devel openssl openvpn

3- Baixar os arquivos com:
wget https://swupdate.openvpn.org/community/releases/openvpn-2.5.5.tar.gz

4- descompacte o arquivo:

tar -xvf openvpn-2.5.5.tar.gz

5- entre no diretório e execute:

cd openvpn-2.5.5
./configure
make
make install

6- adicionar ao /etc/ssl/openssl.conf
[openssl_init] 
providers = provider_sect 

[provider_sect] 
default = default_sect legacy = legacy_sect 

[default_sect] 
activate = 1 

[legacy_sect]
activate = 1

7- mova seus arquivos .conf para /etc/openvpn/server

8- utilize o comando e nome do arquivo para habilitar e iniciar:

systemctl enable openvpn-server@[filename]
systemctl start openvpn-server@[filename]
