## buat RSA key pair dengan meng-generate dari client

ssh-keygen

## copy public key hasil dari generate key pair

ssh-copy-id [username]@[ip-server]

## verifikasi public key hasil copy dari client pada server

cat ~/.ssh/authorized_keys

## verifikasi ssh dari client ke server

ssh [username]@[ip-server]

## menghubah port ssh

nano /etc/ssh/sshd_config

uncomment
```
#Port 22
```

edit
```
Port 2200
```

## ssh dengan port

ssh -p 2200 [username]@[ip-server]

## mengizinkan login dengan root

uncomment
```
PermitRootLogin prohibit-password
```

edit
```
PermitRootLogin yes
```