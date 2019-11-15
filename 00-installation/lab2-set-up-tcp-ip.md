## menampilkan interface yang ada

ip link

## menampilkan pengaturan interface

cat /etc/network/interfaces

## masuk sebagai root

su -

## backup konfirugrasi

cp /etc/network/interfaces /etc/network/interfaces.bak

## ubah konfigurasi ip menjadi statis

nano /etc/network/interfaces

auto ens33
iface ens33 inet static
address 192.168.254.19/24
gateway 192.168.254.1
dns-nameservers 8.8.8.8

## restart interface

systemcl restart networking

## merubah dns server dari resolv.conf

nano /etc/resolv.conf

nameserver 8.8.8.8    
nameserver 8.8.4.4

## menguji koneksi

ping -c 3 8.8.8.8

## konfigurasi ip address dhcp

nano /etc/network/interfaces

auto ens33
allow-hotplug ens33
iface ens33 inet dhcp