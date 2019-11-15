## instalasi paket apache2 pada server

apt update
apt install -y apache2

## verifikasi service apache2 pada server

systemctl status apache2

## verifikasi webserver dari server

apt install -y w3m

w3m http://[ip-server]

q <- quit

## verifikasi service apache2 pada web browser client

http://[ip-server]