## install bind9

apt install -y bind9

## konfigurasi bind server

vim /etc/bind/named.conf.default-zones

**add**
```
zone "144.16.172.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0.144.16.172";
};

zone "kudaliar.local" {
	type master;
	file "/etc/bind/db.kudaliar.local";
};
```

## buat domain zones untuk name resolution

vim /etc/bind/db.kudaliar.local

```
;
; BIND data file for kudaliar.local
;
$TTL	604800
@	IN	SOA	kudaliar.local. root.kudaliar.local. (
			      1		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	kudaliar.local.
@	IN	A	172.16.144.130
www	IN	A	172.16.144.130
```

## buat domain zone untuk address resolution

vim /etc/bind/db.0.144.16.172

```
;
; BIND reverse data file for kudaliar.local
;
$TTL	604800
@	IN	SOA	kudaliar.local. root.kudaliar.local. (
			      1		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	kudaliar.local.
130	IN	PTR	kudaliar.local.
130	IN	PTR	www.kudaliar.local.
```

## restart bind server

systemctl restart bind9

## ubah dns server

vim /etc/resolv.conf

**add**
nameserver 172.16.144.130

## verifikasi name resolution apakah berjalan dengan benar

dig kudaliar.local

## verifikasi address resolution apakah berjalan dengan benar

dig -x 172.16.144.130

## setup cname in zone

vim /etc/bind/db.kudaliar.local

**add**
```
ftp	IN	CNAME	kudaliar.local.
```

## verifikasi domain baru yang ditambahkan

dig ftp.kudaliar.local