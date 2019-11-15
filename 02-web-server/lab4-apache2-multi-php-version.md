## instal paket library libapache2-mod-fcgid

apt install -y libapache2-mod-fcgid

## tambahkan repositori php 5.6

apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://packages.sury.org/php/apt.gpg | apt-key add -
add-apt-repository "deb https://packages.sury.org/php/ $(lsb_release -cs) main"
apt update

## install php5.6 dan php fpm

apt install -y php5.6 php5.6-fpm php7.0-fpm

## verifikasi instalasi paket php-fpm

ls /var/run/php

## aktifkan module fcgi pada apache2

a2enmod actions alias proxy_fcgi fcgid

## restart service apache2 pada server

systemctl restart apache2

## atur file konfigurasi virtualhost agar dapat membaca 2 versi php

nano /etc/apache2/sites-enabled/domain.conf

**add**
```
<Location /php5>
	SetHandler "proxy:unix:/var/run/php/php5.6-fpm.sock|fcgi://localhost/"
</Location>
<Location /php7>
	SetHandler "proxy:unix:/var/run/php/php7.0-fpm.sock|fcgi://localhost/"
</Location>
```

apache2ctl configtest

systemctl restart apache2

mkdir /var/www/domain/php5
mkdir /var/www/domain/php7

## tambahkan file index untuk masing-masing direktori versi php

echo "<?php phpinfo();" > /var/www/kudaliar.local/php5/index.php
echo "<?php phpinfo();" > /var/www/kudaliar.local/php7/index.php

## testing melalui browser

http://domain/php5/
http://domain/php7/