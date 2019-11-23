## instalasi paket mariadb pada server

apt install -y mariadb-server

## jalankan konfigurasi awal mariadb

mysql_secure_installation

```
Change the root password? [Y/n] Y

Remove anonymous users? [Y/n] y

Disallow root login remotely? [Y/n] y

Remove test database and access to it? [Y/n] y

Reload privilege tables now? [Y/n] y
```

## verifikasi service mariadb

systemctl status mysql

## masuk ke dalam database mariadb dengan user root

mysql

## menampilkan list user pada database

MariaDB [(none)]> select user, host, password from mysql.user;

## membuat database baru

MariaDB [(none)]> create database tefa;

## menampilkan list database

MariaDB [(none)]> show databases;

## membuat user baru pada database

MariaDB [(none)]> create user [username]@'%' identified by [password];

## verifikasi user baru pada database;

MariaDB [(none)]> select user, host, password from mysql.user;

## assign hak akses penuh pada user baru

MariaDB [(none)]> grant all privileges on *.* to [username]@'%';

## verifikasi hak akses pada user baru

MariaDB [(none)]> show grants for [username]@'%';

## test login menggunakan user baru

mysql -u [username] -p

## buat table pada database

use tefa;

MariaDB [tefa]> create table table_tefa (
    -> col1 int
    -> );

## verifikasi table dalam database

MariaDB [tefa]> show tables;