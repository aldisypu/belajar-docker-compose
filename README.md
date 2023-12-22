# DOCKER COMPOSE
### Membuat container
```docker
docker compose create
```

### Menjalankan container
```docker
docker compose start
```

### Melihat container
```docker
docker compose ps
```

### Menghentikan container
```docker
docker compose stop
```

### Menghapus container
```docker
docker compose down
```

### Untuk melihat daftar project yang sedang berjalan
```docker
docker compose ls
```

### Menghapus volume
```docker
docker volume rm nama-volume
```

### Depends On
- Kita bisa membuat urutan menjalankan Container dengan menggunakan attribute depends_on
- Kita bisa sebutkan pada Container, bahwa Container ini hanya bisa berjalan, kalo Container yang 
- lain sudah berjalan

### Restart
- no: default nya tidak pernah restart
- always: selalu restart jika container berhenti, tapi jika di hentikan manual, dia akan restart ketika
- pertama kali docker restart
- on-failure: restart jika container error dengan indikasi error ketika exit
- unless-stopped: selalu restart container, kecuali ketika dihentikan manual

### Monitor Docker Events
docker events
- Contohnya kita bisa memonitor kejadian yang terjadi pada sebuah contanier dengan perintah :
```docker
docker events --filter ‘container=nama’
```

### Resource Limit
- reservation adalah resource yang dijamin bisa digunakan oleh container
- limit adalah limit maksimal untuk resource yang diberikan ke container, namun ingat bisa saja limit
- ini rebutan dengan container lain



# DOCKERFILE

### Build Dockerfile
- Ketika kita menggunakan perintah `docker compose start`, secara otomatis Docker Compose akan
- melakukan build terlebih dahulu jika Image nya belum terbuat
- Tapi jika kita hanya ingin melakukan build Image saja, tanpa membuat Container, kita juga bisa
```docker
docker compose build
```

### Menghapus Image
```docker
docker image rm nama-image:tag
```

### Build Ulang
- Perlu diingat, ketika kita mengubah kode program, lalu kita coba stop dan start ulang container
- menggunakan Docker Compose, bukan berarti kode program terbaru akan berjalan
- Hal ini karena Image versi baru otomatis terbuat, sehingga jika kita kita ingin menggunakan Image
- versi baru, kita harus hapus dulu Container nya, lalu buat ulang dengan Image baru

### Disable Health Check
- Cukup di attribute healthcheck, tambahkan attribute disabled: true



### Extend Service
- Saat menjalankan Docker Compose, kita bisa gunakan perintah `-f namafile.yaml` jika ingin
- menggunakan nama file yang bukan docker-compose.yaml
```docker
docker compose -f docker-compose.yaml -f dev.yaml create
docker compose -f docker-compose.yaml -f dev.yaml start
```