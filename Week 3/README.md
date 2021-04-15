# Task Dev Ops

Jouzie Aulia Rezky - DWDS04JAR

Week 3 - Docker & CI/CD

- Install Docker
- Create Docker Images
- Install Application
- Install Jenkins
- Create Jenkins Job

# Install Docker

Saya menginstall di Instance `FRONTEND - PRIVATE` terlebih dahulu, baru di `BACKEND - PRIVATE`

1. Pastikan sudah lakukan terdaftar di `hub.docker.com`

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

7. Jika sudah berjalan dengan baik, mencoba login Docker dengan command `sudo docker login`, lalu memasukan username dan password yang sudah didaftarkan di `hub.docker.com`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-21-55-153.jpg)

Docker di Instance `FRONTEND - PRIVATE` sudah berhasil diinstal, selanjutnya meng-install Docker di `BACKEND - PRIVATE`, akses Instance tersebut.

8. Set-up Repository seperti ini untuk instalasi Docker

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

9. Memasang GPG Key Resmi dari Docker dengan command: 

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-23-32-471.jpg)

10. Menambahkan Stable Repository untuk Docker dengan command berikut:

```
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-23-50-907.jpg)

11. Meng-install Docker Engine dengan command berikut:

```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-24-15-856.jpg)

12. Jika sudah, memastikan apakah Docker sudah terinstall sempurna apa belum dengan cara mengecek versi dengan command `docker -v`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-24-47-394.jpg)

13. Jika sudah berjalan dengan baik, mencoba login Docker dengan command `sudo docker login`, lalu memasukan username dan password yang sudah didaftarkan di `hub.docker.com`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%203/img1/bandicam%202021-04-16%2001-25-01-686.jpg)



























