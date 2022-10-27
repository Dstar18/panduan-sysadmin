

## Deploy aplikasi Nodejs


1. Install nodejs dan npm.
```
sudo apt-get install -y nodejs npm
```

2. Buat direktori nodejs aplikasi dan masuk
```
mkdir nodeapp
cd nodeapp
```

3. Inisialisasi express js project dengan mengetikan.
```
npm init
```
Lalu ikuti instruksi isian yang ada.
Kemudian  install express
```
npm install --save express
```

4. Buat file server.js dengan script berikut
```
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

5. Jalankan 
```npm run start``` untuk start project secara manual


## Membuat init system agar berjalan secara manual

1. Buat file pada ```/etc/systemd/system/nodeapp.service``` dengan isi berikut

```
[Unit]
Description=Prometheus exporter for machine metrics
[Service]
Restart=always
User=ubuntu
ExecStart=node /path/to/project/server.js
ExecReload=/bin/kill -HUP $MAINPID
TimeoutStopSec=20s
SendSIGKILL=no
[Install]
WantedBy=multi-user.target
```

2. Jalankan command berikut agar bisa jalan saat booting

```
sudo systemctl daemon-reload
sudo systemctl start nodeapp.service
sudo systemctl enable nodeapp.service
```
