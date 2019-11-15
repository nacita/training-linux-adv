## backup source.list

cp /etc/apt/sources.list /etc/apt/sources.list.bak

## edit source list

comment 
```
# deb cdrom:[Debian GNU/Linux 9.11.0 _Stretch_ - Official amd64 DVD Binary-1 20190908-18:12]/ stretch contrib main
```

uncomment
```
deb http://deb.debian.org/debian/ stretch-updates main contrib
deb-src http://deb.debian.org/debian/ stretch-updates main contrib
```

add
```
deb http://deb.debian.org/debian/ stretch main contrib non-free
deb-src http://deb.debian.org/debian/ stretch main contrib non-free
```

## update repositori

apt update

## upgrade debian

apt upgrade

## install vim

apt install -y vim