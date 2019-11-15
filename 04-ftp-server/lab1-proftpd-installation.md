## instalasi paket proftpd

apt install -y proftpd

## atur konfigurasi proftpd

vim /etc/proftpd/proftpd.conf

**uncomment**
```
DefaultRoot                   ~
```

systemctl restart proftpd

## buat sistem user untuk login ftp

adduser [username]

## verifikasi proftpd pada filezilla client