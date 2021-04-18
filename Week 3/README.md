# Task Dev Ops

Jouzie Aulia Rezky - DWDS04JAR

Week 3 - Docker & CI/CD

- [Install Docker](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/README.md#install-docker)
- [Create Docker Images](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/README.md#create-docker-image)
- [Install Application](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/README.md#install-application)
- Install Jenkins
- Create Jenkins Job

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





























