# Task Dev Ops

Jouzie Aulia Rezky - DWDS04JAR

Week 3 - Docker & CI/CD

- [Install Docker](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/README.md#install-docker)
- [Create Docker Images](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/README.md#create-docker-image)
- [Install Application](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/README.md#install-application)
- [Install Jenkins](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/README.md#install-jenkins)
- [Create Jenkins Job](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/README.md#create-jenkins-job)

# Install Docker

Saya menginstall di Instance `FRONTEND - PRIVATE` terlebih dahulu, baru di `BACKEND - PRIVATE`

1. Pastikan sudah daftar akun Docker di `hub.docker.com`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-08-09-995.jpg)

2. Akses Instance `FRONTEND - PRIVATE`, lalu mulai Set-up Repository seperti ini untuk instalasi Docker

```
sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-16-00-683.jpg)

3. Memasang GPG Key Resmi dari Docker dengan command: 

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-16-34-553.jpg)

4. Menambahkan Stable Repository untuk Docker dengan command berikut:

```
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-19-33-562.jpg)

5. Meng-install Docker Engine dengan command berikut:

```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-19-40-537.jpg)

6. Jika sudah, memastikan apakah Docker sudah terinstall sempurna apa belum dengan cara mengecek versi dengan command `docker -v`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-20-16-387.jpg)

7. Meng-instal Docker Compose dengan command:

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2002-12-39-357.jpg)

8. Jika sudah berjalan dengan baik, mencoba login Docker dengan command `sudo docker login`, lalu memasukan username dan password yang sudah didaftarkan di `hub.docker.com`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-21-55-153.jpg)

Docker di Instance `FRONTEND - PRIVATE` sudah berhasil diinstal, selanjutnya meng-install Docker di `BACKEND - PRIVATE`, akses Instance tersebut.

9. Set-up Repository seperti ini untuk instalasi Docker

```
sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-23-21-636.jpg)

10. Memasang GPG Key Resmi dari Docker dengan command: 

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-23-32-471.jpg)

11. Menambahkan Stable Repository untuk Docker dengan command berikut:

```
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-23-50-907.jpg)

12. Meng-install Docker Engine dengan command berikut:

```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-24-15-856.jpg)

13. Jika sudah, memastikan apakah Docker sudah terinstall sempurna apa belum dengan cara mengecek versi dengan command `docker -v`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-24-47-394.jpg)

14. Meng-instal Docker Compose dengan command:

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2002-13-38-692.jpg)

15. Jika sudah berjalan dengan baik, mencoba login Docker dengan command `sudo docker login`, lalu memasukan username dan password yang sudah didaftarkan di `hub.docker.com`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-25-01-686.jpg)

Instalasi Docker di kedua Instance telah selesai.

# Create Docker Image

Membuat Docker Image terhadap `wayshub-frontend` dan `wayshub-backend`

1. Masuk ke Instance `FRONTEND - PRIVATE` lalu masuk ke directory `wayshub-frontend` dan buat file baru bernama `Dockerfile`.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img2/bandicam%202021-04-16%2005-19-44-179.jpg)

2. Edit file `Dockerfile` seperti ini.

```
FROM node:14
WORKDIR /usr/src/app
COPY . .
RUN npm i & npm run build
EXPOSE 3000
CMD ["npm","start"]
```

Jika sudah, save overwrite

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img2/bandicam%202021-04-16%2005-19-47-593.jpg)

3. Melakukan Build Docker Images `wayshub-frontend` dengan command:

```
sudo docker build -t aureezzhenx/wayshub-frontend:v1.0.0 .
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img2/bandicam%202021-04-16%2005-23-42-440.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img2/bandicam%202021-04-16%2005-23-52-319.jpg)

4. Melakukan Push Docker Images ke Repository `hub.docker.com` yang sudah di Build sebelumnya dengan command:

```
sudo docker push aureezzhenx/wayshub-frontend:v1.0.0
```

Build Docker Images untuk `wayshub-frontend` telah selesai, selanjutnya di `wayshub-backend`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img2/bandicam%202021-04-16%2005-25-25-341.jpg)

5. Masuk ke Instance `BACKEND - PRIVATE` lalu masuk ke direktori `wayshub-backend` dan buat file baru `Dockerfile`, lalu edit seperti ini

```
FROM node:14
WORKDIR /usr/src/app
COPY . .
EXPOSE 5000
CMD ["npm","start"]
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img2/bandicam%202021-04-16%2005-28-55-670.jpg)

6. Melakukan Build Docker Images `wayshub-backend` dengan command:

```
sudo docker build -t aureezzhenx/wayshub-backend:v1.0.0 .
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img2/bandicam%202021-04-16%2005-30-56-583.jpg)

7. Melakukan Push Docker Images ke Repository `hub.docker.com` yang sudah di Build sebelumnya dengan command:

```
sudo docker push aureezzhenx/wayshub-backend:v1.0.0
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img2/bandicam%202021-04-16%2005-31-38-573.jpg)

8. Akses Repository di `hub.docker.com`, Repository `wayshub-frontend` dan `wayshub-backend` telah sukses di Push

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img2/bandicam%202021-04-16%2005-31-57-560.jpg)


# Install Application

Catatan: Saya sebelum melakukan task ini, saya sudah mematikan aplikasi `wayshub-frontend` dan `wayshub-backend` lewat `pm2` dengan command `pm2 stop wayshub-backend` (Backend) dan `pm2 stop wayshub` (Frontend) agar port yang diekspos tidak bentrok.

1. Masuk ke Instance `BACKEND - PRIVATE` lalu ketik command berikut:

```
# Untuk melihat Images Docker yang sudah dibuat/sudah di download dari hub.docker.com
sudo docker images

# Membuat Container Docker Baru
sudo docker container create --name wayshub-backend -p 5000:5000 aureezzhenx/wayshub-backend:v1.0.0

# Mengecek semua list Container yang status nya Created/Exited/Run
sudo docker container ls --all

# Menjalankan Container yang sebelumnya dibuat
sudo docker container start wayshub-backend

# Mengecek Log, apakah Container sudah berjalan dengan baik atau belum
sudo docker container logs wayshub-backend
```

Container untuk Wayshub-Backend sudah berjalan dengan baik, sekarang lakukan untuk Wayshub-Frontend

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img3/bandicam%202021-04-18%2016-17-44-955.jpg)

2. Masuk ke Instance `FRONTEND - PRIVATE` lalu ketik command berikut:

```
# Untuk melihat Images Docker yang sudah dibuat/sudah di download dari hub.docker.com
sudo docker images

# Membuat Container Docker Baru
sudo docker container create --name wayshub-frontend -p 3000:3000 aureezzhenx/wayshub-frontend:v1.0.0

# Mengecek semua list Container yang status nya Created/Exited/Run
sudo docker container ls --all

# Menjalankan Container yang sebelumnya dibuat
sudo docker container start wayshub-frontend

# Mengecek Log, apakah Container sudah berjalan dengan baik atau belum
sudo docker container logs wayshub-frontend
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img3/bandicam%202021-04-18%2016-19-46-042.jpg)

Container untuk Wayshub-Frontend dan Wayshub-Backend kini sudah berjalan dengan baik.

3. Akses aplikasi yang sudah berjalan di Container

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img3/bandicam%202021-04-18%2016-20-02-553.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img3/bandicam%202021-04-18%2016-20-11-687.jpg)

# Install Jenkins

1. Akses `awseducate.com` lalu buat Instance untuk `JENKINS CI/CD - PRIVATE`, nantinya `Jenkins` akan diinstal di instance sana.

Catatan:

```
1. Security Group Instance: All Traffic
2. Subnet Instance: Memakai Subnet Private sebelumnya.
3. Auto assigned Public Instance: Disabled
4. Type Instance: t2.large
5. Storage Instance: 30GB
6. Instance memakai Key-Pair yang sama, JouzieAuliaRezky.pem
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-34-30-441.jpg)

2. Akses Instance `JENKINS CI/CD - PRIVATE` dengan keypair `JouzieAuliaRezky.pem`. Seperti biasa, lakukan adduser agar tidak menggunakan Key-Pair lagi disaat Log-in Instance tersebut.

Command:

```
1. sudo adduser jouziejenkins
2. Memasukan Password UNIX dan mengisi biodata User
3. sudo usermod -aG sudo jouziejenkins
4. sudo nano /etc/ssh/sshd_config
5. Merubah menjadi YES di Password Authentication, save overwrite
6. sudo systemctl restart sshd
```

Dan lakukan `sudo apt update` dan `sudo apt upgrade` setelah melakukan `adduser`

3. Install OpenJDK 8 dengan command: `sudo apt-get install openjdk-8-jdk`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-35-54-680.jpg)

4. Lakukan ini, Command:

```
# Menambahkan Key Repository Jenkins
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -

# Menambahkan Repository Jenkins
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

# Jalankan apt-get update
sudo apt-get update

# Install Jenkins
sudo apt-get install jenkins

# Menjalankan Jenkins
sudo systemctl start jenkins

# Melihat Status Jenkins
sudo systemctl status jenkins
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-37-34-318.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-39-10-744.jpg)

`jenkins` sudah terinstall dengan port `8080`, tapi belum bisa di akses secara public karena Instance `JENKINS CI/CD - PRIVATE` tidak ada IP Public-nya. Sekarang lakukan reverse proxy terhadap `jenkins` di Instance `REVERSE PROXY - PUBLIC`

5. Sebelum melakukan Reverse Proxy, akses `dash.cloudflare.com` terlebih dahulu untuk membuat New Records Baru. Saya membuat 2 Records

```
# Record CICD untuk Reverse Proxy
Type: A
Name: cicd.jouzie
IPv4 Address: 54.162.149.199
TTL: Auto
Proxy: DNS Only

# Record CICD untuk Server Private
Type: A
Name: cicdserver.jouzie
IPv4 Address: 172.31.62.162
TTL: Auto
Proxy: DNS Only
```

Alasan saya membuat Record untuk Instance `JENKINS CI/CD - PRIVATE`, karena agar memudahkan saya melakukan Aktifitas Log-in, Reverse Proxy tanpa perlu Copy-Paste IP Private nya.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-39-25-697.jpg)

6. Masuk ke Instance `REVERSE PROXY - PUBLIC`, lalu jalankan command `cerbot` berikut untuk meng-instal sertifikat di subdomain `cicd.jouzie.onlinecamp.id`

```
sudo certbot certonly --dns-cloudflare --dns-cloudflare-credentials ~/.secrets/cloudflare.ini -d cicd.onlinecamp.id
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-42-59-852.jpg)

7. Masuk ke direktori `/etc/nginx/` lalu buat direktori baru yaitu `cicd` dengan command `sudo mkdir cicd`, masuk ke direktory tersebut lalu lakukan nano `cicd.conf` dengan command `sudo nano cicd.conf`

Copy-Paste config ini:

```
server
{
        server_name cicd.jouzie.onlinecamp.id;

        location /
        {
                proxy_pass http://cicdserver.jouzie.onlinecamp.id:8080;
        }

    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/cicd.jouzie.onlinecamp.id/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/cicd.jouzie.onlinecamp.id/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
}
```

Jika sudah, save overwrite dengan nama file `cicd.conf`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2019-02-41-6077.jpg)

8. Edit file `nginx.conf` di direktory `/etc/nginx/` dengan command `sudo nano nginx.conf`. Tambahkan Include baru untuk `cicd`

```
include /etc/nginx/cicd/*;
```

Jika sudah, save overwrite.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-48-39-018.jpg)

9. Lakukan Restart `nginx` dengan command:

```
sudo nginx -t
sudo systemctl restart nginx
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-49-54-804.jpg)

10. Jalankan `sudo certbot` untuk me-registrasi SSL terhadap sub-domain `cicd.jouzie.onlinecamp.id`. Pilih nomor urutan 3

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-50-27-535.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-50-27-583.jpg)

11. Akses `jenkins` dengan URL `https://cicd.jouzie.onlinecamp.id`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-59-19-424.jpg)

12. Lakukan Unlock Jenkins dengan mengecek file `InitialAdminPassword` di direktori `/var/lib/jenkins/secrets/initialAdminPassword` dengan command `sudo cat /var/lib/jenkins/secrets/initialAdminPassword`. Copy `InitialAdminPassword` yang didapat.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2018-59-58-801.jpg)

13. Paste `InitialAdminPassword` nya

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2019-00-14-626.jpg)

14. Memilih `Install suggested plugins`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2019-00-23-594.jpg)

15. Proses Install Plugin 

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2019-00-31-647.jpg)

16. Membuat akun Admin User untuk pertama kalinya di Jenkins

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2019-02-18-149.jpg)

17. Mengisi URL Jenkins, default-nya sudah terisi automatis oleh Jenkins

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2019-02-30-358.jpg)

18. Instalasi Jenkins sudah berhasil

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2019-02-34-419.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img4/bandicam%202021-04-18%2019-02-41-607.jpg)

# Create Jenkins Job

Alur Jobs:

```
1. Pull/Push Wayshub yang sudah ada Dockerfile ke Github
2. Jenkins menerima Trigger dari Github
3. Jenkins melakukan Auto Build Docker Images
4. Push ke Repository Docker Hub
5. Jenkins masuk SSH Frontend
6. Pull Docker Images dari Docker Hub
7. Create Container
8. Start Container
```

1. Memasang Plugin Docker (CloudBees Docker Build and Publish plugin)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-17-45-375.jpg)

2. Membuat Jobs Baru untuk Frontend, dengan memilih `Freestyle project`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-18-09-804.jpg)

3. Melakukan Konfigurasi

```
1. Github Project: https://github.com/aureezzhenx/wayshub-frontend
2. Repository URL: https://github.com/aureezzhenx/wayshub-frontend.git
3. Branch Specifier: */main
4. Checklist GITHUB HOOK TRIGGER FOR GITSCM POLLING
5. Poll SCM: * * * * * (every minutes)
6. Add Build: Docker Build And Publish
7. Repository Name: aureezzhenx/wayshub-frontend 
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-18-21-176.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-18-23-768.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-18-26-659.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-18-29-244.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-18-37-723.jpg)

4. Buka halaman Repository yang ingin di-trigger Jenkins, klik Settings

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-19-29-558.jpg)

5. Pada sisi kiri menu, klik `Webhooks`, lalu buat `Webhooks` baru. Isi seperti dibawah ini:

```
Payload URL: https://cicd.jouzie.onlinecamp.id/github-webhook/
Content Type: application/json
Memilih Let me select Individual Events (Pull Request & Pushes)
```

Jika sudah, Accept.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-19-57-345.jpg)

6. Melakukan test Trigger ke Jenkins, dengan mengubah file Readme

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-20-38-463.jpg)

7. Jenkins menerima Trigger dari Repository Github yang sudah terkoneksi oleh Webhooks, dan melakukan Job nya

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-20-48-640.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-20-54-325.jpg)

8. Proses Job dari Jenkins tengah berlangsung, Job sedang melakukan Build Docker Images.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-20-59-884.jpg)

9. Proses Build sudah selesai.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-22-16-257.jpg)

10. Lalu cek di Repository Docker Hub. Karena sebelumnya tidak mengisi Tag Versi disaat konfigurasi Build Job. Oleh karena itu, dianggap sebagai `latest` Tag.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img5/bandicam%202021-04-19%2001-22-35-282.jpg)





































