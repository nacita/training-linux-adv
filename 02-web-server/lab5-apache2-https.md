## buat self-signed certificate untuk apache2 pada server

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/apache-selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt

```
Country Name (2 letter code) [AU]:ID
State or Province Name (full name) [Some-State]:Jawa-Timur
Locality Name (eg, city) []:Malang
Organization Name (eg, company) [Internet Widgits Pty Ltd]:DOT Indonesia
Organizational Unit Name (eg, section) []:SysAdmin
Common Name (e.g. server FQDN or YOUR name) []:[domain]
Email Address []:admin@[domain]
```

## ubah file konfigurasi virtualhost domain yang dibuat sebelumnya

nano /etc/apache2/sites-enable/[domain].conf

**add**
```
<VirtualHost *:443>
        ServerAdmin admin@[domain]
        ServerName [domain]

        DocumentRoot /var/www/[domain]

        ErrorLog ${APACHE_LOG_DIR}/[domain]-error.log
        CustomLog ${APACHE_LOG_DIR}/[domain]-access.log combined

        SSLEngine on
        SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
        SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key

        <Location /php5>
                SetHandler "proxy:unix:/var/run/php/php5.6-fpm.sock|fcgi://localhost/"
        </Location>
        <Location /php7>
                SetHandler "proxy:unix:/var/run/php/php7.0-fpm.sock|fcgi://localhost/"
        </Location>
</VirtualHost>
```

## aktifkan modul ssl

a2enmod ssl

## test konfigurasi

apache2ctl configtest

## restart apache

systemctl restart apache2

## verifikasi pada web browser client

https://[domain]

## redirect url http ke https pada apache2

nano /etc/apache2/sites-enable/[domain].conf

**edit**
```
<VirtualHost *:80>
        ServerAdmin admin@[domain]
        ServerName [domain]

        Redirect / https://[domain]/
</VirtualHost>
```

## test konfigurasi

apache2ctl configtest

## restart service apache2 pada server

systemctl restart apache2

## verifikasi pada web browser client

http://[domain]
