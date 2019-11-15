## menampilkan interface yang ada

ip link

## menampilkan pengaturan interface

cat /etc/network/interfaces

## masuk sebagai root

su -

## backup konfirugrasi

cp /etc/network/interfaces /etc/network/interfaces.bak

## instal resolveconf

apt install -y resolveconf

## ubah konfigurasi ip menjadi statis

nano /etc/network/interfaces

auto enp0s3
iface enp0s3 inet static
address 192.168.254.19/24
gateway 192.168.254.1
dns-nameservers 8.8.8.8

## restart interface

systemcl restart networking

## menguji koneksi

ping -c 3 8.8.8.8

## konfigurasi ip address dhcp

nano /etc/network/interfaces

auto enp0s3
allow-hotplug enp0s3
iface enp0s3 inet dhcp

## restart networking

systemctl restart networking