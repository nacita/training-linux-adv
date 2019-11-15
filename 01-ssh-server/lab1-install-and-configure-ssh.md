## install paket openssh

apt install -y openssh-server

## jalankan service ssh

systemctl start ssh

## verifikasi status service ssh

systemctl status ssh

## akses ssh dari client ke server

ssh [username]@[ip-server]