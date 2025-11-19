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

