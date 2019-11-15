# BACKUP

## backup menggunakan perintah mysqldump

mysqldump tefa > ~/backup_db_tefa.sql

## verifikasi file backup

ls -l ~/

# RESTORE

## buat database baru pada mariadb

mysql

MariaDB [(none)]> create database tefa1;

MariaDB [(none)]> exit;

## restore file backup pada database yang baru saja dibuat

mysql tefa1 < ~/backup_db_tefa.sql

## verifikasi database tefa1

mysql

MariaDB [(none)]> use tefa1;

MariaDB [tefa1]> show tables;

# BACKUP OTOMATIS

## install automysqlbackup

apt install -y automysqlbackup 

## jalankan automysqlbackup untuk pertama kali

automysqlbackup

## verifikasi hasil backup otomatis

ls -a /var/lib/automysqlbackup/daily

## cek file konfigurasi dari automysqlbackup

nano /etc/default/automysqlbackup

## pindah direktori backup automysqlbackup

nano /etc/default/automysqlbackup

**edit**
```
BACKUPDIR="/database_bkp/"
```

mkdir /database_bkp

## test backup lagi

automysqlbackup

## verifikasi hasil backup

ls -a /database_bkp/daily