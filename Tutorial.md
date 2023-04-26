# Adicionando o openvpn-2.5.5 ao fedora 37 e 38

**1- Entre em modo root:**
```bash
su
```

**2- Instale os seguintes pacotes:**
```bash
dnf install lzo-devel pam-devel openssl openvpn
```

**3- Baixar os arquivos com:**
```bash
wget https://swupdate.openvpn.org/community/releases/openvpn-2.5.5.tar.gz
```

**4- descompacte o arquivo:**
```bash
tar -xvf openvpn-2.5.5.tar.gz
```

**5- entre no diretório e execute:**
```bash
cd openvpn-2.5.5
./configure
make
make install
```

**6- Descomentar no arquivo /etc/ssl/openssl.conf**
```bash
[openssl_init] 
providers = provider_sect 

[provider_sect] 
default = default_sect 
legacy = legacy_sect 

[default_sect] 
activate = 1 

[legacy_sect]
activate = 1
```

**7- mova seus arquivos .conf para /etc/openvpn/server**
```bash
cp *.ovpn
mv [filename].ovpn [filename].conf
mv filename.conf /etc/openvpn/server
```
**8- utilize o comando e nome do arquivo para habilitar e iniciar:**
```bash
systemctl enable openvpn-server@[filename]
systemctl start openvpn-server@[filename]
```

**OBs**: não é recomendado a atualização completa de pacotes, sempre se utlizando do dnfdragora ou a exclusão do pacote durante a atualização via linha de comando.
