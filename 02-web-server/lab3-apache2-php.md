## instalasi paket php pada server

apt install -y php

## buat agar apache2 memprioritaskan file index.php

nano /etc/apache2/mods-enabled/dir.conf

**edit**
```
<IfModule mod_dir.c>
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
```

## restart service apache2 pada server

systemctl restart apache2
systemctl status apache2

## verifikasi php sudah dapat digunakan

touch /var/www/kudaliar.local/info.php
nano /var/www/kudaliar.local/info.php

```
<?php
        phpinfo();
```

## verifikasi php dari terminal

curl http://domain/info.php

## verifikasi php pada web browser client

http://domain/info.php