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




