#Adding openvpn-2.5.5 to fedora 37 and 38

**1- Enter root mode:**
```bash
su
```
**2- Install the following packages:**
```bash
dnf install lzo-devel pam-devel openssl openvpn
```
**3- Download the files with:**
```bash
wget https://swupdate.openvpn.org/community/releases/openvpn-2.5.5.tar.gz
```
**4- unzip the file:**
```bash
tar -xvf openvpn-2.5.5.tar.gz
```
**5- enter the directory and run:**
```bash
cd openvpn-2.5.5
./configure
make up
make install
```
**6- Uncomment the /etc/ssl/openssl.conf file**
```bash
[openssl_init]
providers = provider_sect

[provider_sect]
default = default_sect legacy = legacy_sect

[default_sect]
activate = 1

[legacy_sect]
activate = 1
```
**7- move your .conf files to /etc/openvpn/server**
```bash
cp *.ovpn
mv [filename].ovpn [filename].conf
mv filename.conf /etc/openvpn/server
```
**8- use the command and file name to enable and start:**
```bash
systemctl enable openvpn-server@[filename]
systemctl start openvpn-server@[filename]
```
***Note***: it is not recommended to update the packages completely, always using dnfdragora or to exclude the package during the update via the command line.
