# network-lab-Modulo-7

Laboratorios del modulo VII Practica 1

sudo apt install nfs-kernel-server

sudo mkdir -p /srv/OS3/

cd /srv/OS3/

sudo touch Adrian{1..100}.txt

ls 

sudo chown -R nobody:nogroup /srv/OS3

sudo chmod 755 /srv/OS3

sudo nano /etc/exports

/srv/OS3 192.168.7.120/24(rw,sync,no_subtree_check)

sudo exportfs -a

sudo systemctl restart nfs-kernel-server

sudo apt install nfs-common -y

sudo mkdir -p /mnt/OS3

sudo mount 192.168.7.121:/srv/OS3 /mnt/OS3

ls /mnt/OS3 

sudo nano /etc/fstab

192.168.1.11:/srv/OS3 /mnt/OS3 nfs defaults 0 0

sudo reboot 

ls /mnt/OS3

sudo touch hola.txt

ls

ls /mnt/OS3

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Laboratorios del modulo VII Practica 2

sudo apt update

sudo apt install samba -y

sudo systemctl enable smdb

sudo systemctl status 

sudo mkdir -p /srv/samba/shared 

sudo groupadd sambashared

sudo useradd -M -S /sbin/nologin adrian1

sudo usermod -aG sambashare adrian1

sudo smbpasswd -a adrian1

sudo chown -R adrian1:sambashare /srv/samba/shared

sudo chmod -R 770 /srv/samba/shared

sudo nano /etc/samba/smb.conf 

[shared]
   path = /srv/samba/shared
   browseable = yes 
   writable = yes
   valid users = @sambashare
   create mask = 0660
   directory mask = 2770

sudo systemctl restart smbd

cd /srv/samba/shared
for i in $(seq 1 100); do
  touch adrian$i.txt
done

sudo -l

ls

this pc 
computer
map network drive

\\192.168.7.120\shared

sudo chown -R adrian1:sambashare /srv/samba/shared

sudo chmod -R 7770 /srv/samba/shared

ls 

cat adrian99.txt

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Laboratorios del modulo VII Practica 3

hostname sambaus

reboot

hostname 

sudo su

echo "192.168.1.11 OS3.inet" >> /etc/host

dnf -y update 

dnf repolist 

dnf config-manager --disable epel epel-cisco-openh264

dnf -y update 

dnf repolist all 

dnf install epel-release

dnf config-manager --enable ol10_codeready_builder

dnf repolist

dnf install -y oracle-epel-release-eli0

dnf repolist all 

dnf update

sudo dnf makecache 

dnf -y install wget tar gcc make python3-devel 

mkdir -p /samba && cd /samba

ls

tar -zxvf samba-4.16.2.tar.gz && cd samba-4.16.2/

exit 

sudo dnf install -y \

docbook-style-xsl python3-markdown bison dbus-devel flex gdb \

gnutls-devel jansson-devel keyutils-libs-devel krb5-workstation \

libacl-devel libaio-devel libarchive-devel libattr-devel libblkid-devel \

libtasn1 libtasn1-tools libxml2-devel libxslt lmdb-devel openldap-devel \

pam-devel perl perl-ExtUtils-MakeMaker perl-Perse-Yapp popt-devel\

python3-cryptography python3-dns python3-gpg readline-devel rpcgen \

systemd-devel zlib-devel perl-JSON gpgme-devel screen 

sudo su

cd /samba 

ls

cd samba-4.16.2/

./configure --prefix=/usr/local/samba --enable-fhs --with-ads --with-systemd

make -j$(nproc)

make install

export PATH=/usr/local/samba/bin:/usr/local/samba/bin:/usr/local/samba/sbin:$PATH

nano ~/.bash_profile 

PATH=$PATH:$HOME/bin:/usr/local/samba/bin:/usr/local/samba/sbin:$PATH

export PATH

nano ../.bash_profile

PATH=$PATH:$HOME/bin/usr/local/amba/bin:/usr/local/amba/bin:$PATH

export PATH

samba-tool domain provision --use-rfc2307 --interactive --option="interfaces = lo ens33" --option="bind interfaces only=yes"

echo "/usr/local/samba" | sudo tee /etc/ld.so.conf.d/samba.conf 

echo "/usr/local/samba/lib64" | sudo tee -a /etc/ld.so.conf.d/samba.conf

echo "/usr/local/samba/lib" | sudo tee -a /etc/ld.so.conf.d/samba.conf

ldconfig

samba-tool domain provision --use-rfc2307 --interactive --option="interfaces = lo ens33" --option="bind interfaces only=yes"

OS3.inet
lo dejamos asi
lo dejamos asi 
lo dejamos asi 
mi puerta de enlace 

colocamos contrasena 

ping google.com 

ping OS3.inet 

cat /etc/hosts

nslookup OS3.inet 

cp /usr/local/samba/var/lib/samba/private/krb5.conf /etc/krb5.conf 

firewall-cmd --permanent --add-server={ldap,ldaps,Kerberos,dns}

firewall-cmd --permanent --add-port={53,88,135,139,389,445,464,636,3268,3269}/tcp

firewall-cmd --permanent --add-port={53,88,123,138,139,464}/udp
 
firewall-cmd --reload 

samba 

samba-tool domain passwordsetting set --complexity=off

samba-tool domain passwordsettings show 

samba-tool user create lanegracubana 20242332

samba-tool group addmembers "Domain Admins" lanegracubana

OS3.inet

samba-tool dns add 192.168.1.11 OS3.inet www A 192.168.1.12 -U Administrator 









