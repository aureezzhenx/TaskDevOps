# Task Dev Ops

Jouzie Aulia Rezky - DWDS04JAR

Week 2

- [Install Git and SSH Key](https://github.com/aureezzhenx/TaskDevOps/tree/main/Week%202#install-git-and-ssh-key)
- [Setup Database](https://github.com/aureezzhenx/TaskDevOps/tree/main/Week%202#setup-database)
- Deployment Backend Application

# Install Git and SSH Key

Catatan: Saya mengerjakan Task ini di Instance `BACKEND - PRIVATE`

1. Membuat SSH Key baru untuk koneksi ke GitHub. Saya tidak menginstal Git, karena sudah ada. Karena sifat file SSH Key itu tersimpan di direktori `.ssh`, saya langsung eksekusi di direktori tersebut ditambah Commands dibawah ini:

```
1. cd ~/.ssh && ssh-keygen
2. Mengetik nama file SSH Key yang diinginkan, disini saya menyimpan filenya sebagai aureezzhenx.
3. Mengosongkan Passphrase.
4. ssh-add aureezzhenx # Untuk memasang identitas SSH Key yang sudah dibuat
5. cat aureezzhenx.pub # Melihat SSH Key seluruhnya, lalu copy.
```

Catatan: Sebelum melakukan `ssh-add` harus menjalankan command `ssh-agent`. Sebelumnya saya sudah menjalankan command tersebut.

```
eval `ssh-agent -s`
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img/bandicam%202021-04-11%2006-09-55-175.jpg)

2. Pergi menuju Settings Account > SSH and GPG Keys > Add New SSH Keys, lalu paste yang sudah di copy sebelumnya, tanpa mengisi title, Nantinya akan diisi sesuai Keseluruhan SSH Key nya. Jika sudah Add SSH Key

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img/bandicam%202021-04-11%2006-10-49-798.jpg)

3. Jika sudah, lakukan tes koneksi SSH Key ke GitHub yang sudah terpasang identitas nya dengan command `ssh -T git@github.com`. 

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img/bandicam%202021-04-11%2006-11-29-693.jpg)

4. Melakukan Fork Repository `wayshub-backend` dari `sgnd` (https://github.com/sgnd/wayshub-backend). Klik tombol Fork.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img/bandicam%202021-04-11%2006-11-57-667.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img/bandicam%202021-04-11%2006-12-19-668.jpg)

5. Melakukan `git clone` Dengan SSH Protocol dengan command `git clone git@github.com:aureezzhenx/wayshub-backend.git`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img/bandicam%202021-04-11%2006-12-24-886.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img/bandicam%202021-04-11%2006-12-36-475.jpg)

6. Melakukan kegiatan yang diminta task, yaitu `git pull`, `git commit` dan `git push` tanpa menggunakan Username & Password GitHub.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img/bandicam%202021-04-11%2006-54-20-833.jpg)

# Setup Database

1. Akses `awseducate.com` Lalu buat Instance baru untuk `BACKEND - PRIVATE` dan `DATABASE - PRIVATE`, nantinya `mysql` nya akan diinstal di Instance `DATABASE - PRIVATE`, dan dapat diremote di `BACKEND - PRIVATE`

Catatan:

```
1. Security Group kedua Instance: All Traffic & MYSQL (3306) dengan source custom ip 0.0.0.0
2. Subnet kedua Instance: Memakai Subnet Private sebelumnya.
3. Auto assigned Public kedua Instance: Disabled
4. Kedua type Instance: t2.micro
5. Storage kedua Instance: 8GB
6. Kedua Instance memakai Key-Pair yang sama, JouzieAuliaRezky.pem
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/abandicam%202021-04-11%2013-08-46-722.jpg)

2. Login Instance `DATABASE - PRIVATE`, lalu download `mysql-apt-config` dengan menggunakan command `wget` berikut

```
wget https://dev.mysql.com/get/mysql-apt-config_0.8.16-1_all.deb
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-25-29-020.jpg)

3. Memulai instalasi `mysql-apt-config`, ketik command berikut

```
sudo dpkg -i mysql-apt-config_0.8.16-1_all.deb
```

Lalu tampilan nya nanti akan seperti ini. Saya meing-instal MYSQL versi 8.x, lalu memilih rekomendasi MYSQL. Jika sudah, Enter di OK.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-26-19-047.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-26-52-049.jpg)

4. Lakukan update `sudo apt update` dan `sudo apt upgrade` sebelum meng-install `mysql-community-server`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-28-28-041.jpg)

5. Selanjutnya, install `mysql-community-server` dengan command `sudo apt install mysql-community-server`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-28-54-182.jpg)

6. Membuat Password `root` di `mysql`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-29-05-886.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-29-13-308.jpg)

7. Jika sudah, masuk `mysql` dengan command berikut

```
1. mysql -u root -p
2. Masukan Password yang sebelumnya dibuat
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-32-02-899.jpg)

8. Exit `mysql` dengan cara mengetik `exit`. Sekarang untuk melakukan `adduser` seperti biasa.

```
1. sudo adduser jouziedatabase
2. Mengisi Informasi user jouziedatabase
3. sudo usermod -aG sudo jouziedatabase
4. sudo /etc/ssh/sshd_config
5. Merubah PasswordAuthentication menjadi Yes, save overwrite
6. sudo systemctl restart sshd
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-39-34-882.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-39-57-646.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-40-16-857.jpg)

9. Logout Instance `DATABASE - PRIVATE` sekarang melakukan setup di `BACKEND - PRIVATE`. Login di instance Backend

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-46-21-409.jpg)

10. Tambah user seperti biasa untuk `BACKEND - PRIVATE` agar tidak login menggunakan SSH Key-Pair lagi.

```
1. sudo adduser jouziebackend
2. Mengisi Informasi user jouziebackend
3. sudo usermod -aG sudo jouziebackend
4. sudo /etc/ssh/sshd_config
5. Merubah PasswordAuthentication menjadi Yes, save overwrite
6. sudo systemctl restart sshd
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-48-42-429.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-49-50-908.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-10%2016-50-41-925.jpg)

11. Karena di `BACKEND - PRIVATE` belum bisa meremote MYSQL di `DATABASE - PRIVATE`, oleh karena itu diharuskan install `mysql-client-core-5.7` dengan command `sudo apt install mysql-client-core-5.7`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-11%2013-11-27-155.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-11%2013-11-50-611.jpg)

12. Masuk ke Instance `DATABASE - PRIVATE` lalu masuk mysql, membuat database `wayshub`

```
mysql -u root -p
create database wayshub;
show databases;
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-11%2013-14-55-559.jpg)

13. Exit `mysql`. Mengisi `bind-address` secara manual pada file `mysqld.cnf` di direktori `/etc/mysql/mysql.conf.d/mysqld.cnf` agar dapat diremote dari `BACKEND - PRIVATE`

```
1. sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
2. Di bagian [mysqld] tambahkan `bind-adress = 0.0.0.0`. Jika sudah save overwrite
3. Melakukan restart mysql dengan command `sudo systemctl restart mysql`
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-11%2013-27-21-234.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-11%2013-26-48-898.jpg)

14. Masuk kembali ke `mysql`, dan ketik command menambahkan user baru mysql di bawah ini serta agar dapat diremote dari `BACKEND - PRIVATE`

```
CREATE USER 'jouzie'@'172.31.54.248' IDENTIFIED by 'jouzie';
GRANT ALL ON *.* to 'jouzie'@'172.31.54.248';
FLUSH PRIVILEGES;
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-11%2013-35-48-020.jpg)

15. Masuk kembali ke Instance `BACKEND - PRIVATE`, lalu remote mysql ke `DATABASE - PRIVATE` dengan commands berikut:

```
1. mysql -u jouzie -h 172.31.50.114 -p
2. Masukan Password
```

`mysql` di Instance `DATABASE - PRIVATE` kini sudah dapat diremote dari Instance `BACKEND - PRIVATE`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-11%2013-36-12-726.jpg)

# Deployment Backend Application

1. Masuk Instance `BACKEND - PRIVATE`, kemudian mengedit file `config.json` di `wayshub-backend/config/` 

```
sudo nano config.json
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img2/bandicam%202021-04-11%2013-36-12-726.jpg)

2. Hanya merubah yang bagian `development` nya saja, mengisi `username`, `password`, `database`, dan `host` nya. Disesuaikan yang sebelum-sebelumnya. Jika sudah, save overwrite.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2016-58-25-616.jpg)

3. Masuk ke Instance `DATABASE - PRIVATE`, kemudian masuk `mysql prompt` lalu membuat database `wayshub`

```
create database wayshub;
show tables;
use wayshub;
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-00-18-359.jpg)

4. Kembali lagi ke Instance `BACKEND - PRIVATE`, masuk ke directory `wayshub-backend`, setelah itu lakukan instalasi:

```
1. NVM: curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
2. exec bash # Eksekusi Bash NVM
3. nvm -v # Memastikan NVM Berhasil Diinstal
4. nvm install 14 # Menginstall Node 14
5. node -v # Memastikan Node Berhasil Diinstal
6. npm -v # Memastikan Node Package Manager Berhasil Diinstal
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-02-44-755.jpg)

5. Meng-install `sequelize` untuk migrasi table yang diperlukan dari `BACKEND - PRIVATE` menuju sql di `DATABASE - PRIVATE`

```
npm install sequelize-cli
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-14-32-997.jpg)

6. Lakukan command `sequelize db:migrate` di direktori `wayshub-backend` untuk mulai migrasi.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-14-38-263.jpg)

7. Mengecek apakah table sudah di ter-imigrasi dari `BACKEND - PRIVATE` menuju sql `DATABASE - PRIVATE`

```
use wayshub;
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-14-59-480.jpg)

8. Kembali lagi ke Instance `BACKEND - PRIVATE`, lakukan instalasi `pm2` agar `wayshub-backend` berjalan di backgroud.

```
npm install pm2 -g
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-16-49-673.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-16-58-045.jpg)

9. Jalankan command `pm2 ecoysytem` untuk meng-generate file eksekusi `pm2`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-17-56-243.jpg)

10. Edit file `ecosystem.config.js` dengan nano. Dan edit seperti ini:

```
module.exports=
{
      apps:
      [
                {
                         name: 'wayshub',
                         script: 'npm',
                         args: 'start',
                }
      ]
}
```

Jika sudah, save overwrite.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-18-38-835.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-24-51-372.jpg)

11. Jalankan `pm2` dengan command `pm2 start ecosystem.config.js` agar `wayshub-backend` mulai dapat dijalankan di background

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-25-28-733.jpg)

12. Akses `app.pm2.io`, untuk menambahkan Key-Matrics Monitoring untuk `wayshub-backend`. Pilih Bucket yang sebelumnya sudah dibuat.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-27-31-855.jpg)

13. Klik Connect > Copy link pm2 to PM2.io

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-27-46-572.jpg)

14. Paste link nya di Instance `BACKEND - PRIVATE` di direktory `wayshub-backend`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-28-50-646.jpg)

15. `wayshub-backend` Sudah dapat di Monitoring di `app.pm2.io` tanpa perlu Monitoring di Instance `BACKEND - PRIVATE`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-29-27-667.jpg)

16. Masuk ke Instance `FRONTEND - PRIVATE`, lakukan edit file `api.js` dengan `nano` di `/wayshub-frontend/src/config/`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-33-21-569.jpg)

17. Rubah `baseURL` nya menjadi `https://api.jouzie.onlinecamp.id/api/v1`. Jika sudah, save overwrite.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-34-48-991.jpg)

18. Restart `wayshub-frontend` dan `wayshub-backend` di `app.pm2.io`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-37-22-995.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-37-52-002.jpg)

19. Akses `dash.cloudflare.com` Login, pilih akun `sugandaletters@outlook`, lalu buat record baru:

```
Type: A
Name: api.jouzie
IPv4 Address: 54.162.149.199
TTL: Auto
Proxy: DNS Only
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-40-12-724.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-40-26-890.jpg)

20. Masuk ke Instance `REVERSE PROXY - PUBLIC` lalu jalankan command `certbot` berikut untuk meng-instal sertifikat di subdomain `api.jouzie.onlinecamp.id`

```
sudo certbot certonly --dns-cloudflare --dns-cloudflare-credentials ~/.secrets/cloudflare.ini -d jouzie.onlinecamp.id -d '*.jouzie.onlinecamp.id'
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-45-47-572.jpg)

21. Masih di Instace `REVERSE PROXY - PUBLIC`, edit file `frontend.conf` di direktory `/etc/nginx/wayshub/` dengan `nano` yang sebelumnya sudah saya buat untuk me-reverse proxy `wayshub-backend`

```
Menambahkan ini saja:

server
{
        server_name api.jouzie.onlinecamp.id;

        location /
        {
                proxy_pass http://172.31.54.248:5000;
        }

    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/jouzie.onlinecamp.id/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/jouzie.onlinecamp.id/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}
```
Jika sudah, save overwrite, dan lakukan restart pada `nginx`

```
sudo nginx -t
sudo systemctl restart nginx
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-53-24-137.jpg)

22. Jalankan `sudo certbot` untuk me-registrasi SSL terhadap domain `api.jouzie.onlinecamp.id`. Pilih nomor urutan 2

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-57-02-616.jpg)

23. Akses `https://api.jouzie.onlinecamp.id/`. Sukses.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%202/img3/bandicam%202021-04-11%2017-58-35-361.jpg)












