## Install Cyberpanel

- Masuk menggunakan root user
- jalankan script berikut untuk installasi
```sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)```
- Ikuti isian yang harus diisi sampai selesai


## Syarat Bisa digunakan mail server
1. punya PTR record dari ip public yang digunakan, dapat dicek dengan cara jalankan command berikut
```
nslookup {ip_address}
```

2. Tidak block port smtp outgoing.
cek dengan jalankan command
```
nmap gmail-smtp-in.l.google.com -Pn -p 25
```