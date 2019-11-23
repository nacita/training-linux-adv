## atur konfigurasi file proftpd pada server 1

nano /etc/proftpd/proftpd.conf

**uncomment**
```
Include /etc/proftpd/tls.conf
```

## atur konfigurasi file tls untuk proftpd

nano /etc/proftpd/tls.conf

**uncomment**
```
TLSEngine                               on
TLSLog                                  /var/log/proftpd/tls.log
TLSProtocol                             SSLv23
```

**uncomment & edit**
```
TLSRSACertificateFile /etc/ssl/certs/apache-selfsigned.crt
TLSRSACertificateKeyFile /etc/ssl/private/apache-selfsigned.key
```

## restart service proftpd

systemctl restart proftpd

## verifikasi ftp server pada filezilla client

explicit