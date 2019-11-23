## buat direktori untuk domain

mkdir /var/www/[domain]

## isi dengan sebuah file index.html

cd /var/www/[domain]
touch index.html
nano index.html

## buat konfigurasi virtualhost untuk domain yang dibuat

cd /etc/apache2/sites-available
nano [domain].conf

```
<VirtualHost *:80>
    ServerAdmin admin@mail.com     
    ServerName [domain]       
    DocumentRoot /var/www/[domain]     
    ErrorLog ${APACHE_LOG_DIR}/[domain]-error.log
    CustomLog ${APACHE_LOG_DIR}/[domain]-access.log combined
</VirtualHost>
```

## aktifkan file konfigurasi virtualhost

a2ensite [domain].conf

## matikan file konfigurasi virtualhost bawaan apache2

a2dissite 000-default.conf

## verifikasi file konfigurasi pada apache2

apache2ctl configtest

## restart service apache2 pada server

systemctl restart apache2

## verifikasi web apache2 pada terminal

apt install -y curl

nano /etc/hosts

**add**
```
127.0.0.1 [domain]
```

curl http://[domain]

## verifikasi web apache2 pada web browser client

http://[domain]