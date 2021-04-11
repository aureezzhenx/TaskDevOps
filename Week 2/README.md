# Task Dev Ops

Jouzie Aulia Rezky - DWDS04JAR

Week 2

- Install Git and SSH Key
- Setup Database
- Deployment Backend Application

# Install Git and SSH Key

Catatan: Saya mengerjakan Task ini di Private Instance untuk Backend.

1. Membuat SSH Key baru untuk koneksi ke GitHub. Saya tidak menginstal Git, karena sudah ada. Karena sifat file SSH Key itu tersimpan di direktori `.ssh`, saya langsung eksekusi di direktori tersebut ditambah Commands dibawah ini:

```
1. cd ~/.ssh && ssh-keygen
2. Mengetik nama file SSH Key yang diinginkan, disini saya menyimpan filenya sebagai aureezzhenx.
3. Mengosongkan Passphrase.
4. ssh-add aureezzhenx # Untuk memasang identitas SSH Key yang sudah dibuat
5. cat aureezzhenx.pub # Melihat SSH Key seluruhnya, lalu copy.
```

CATATAN: Sebelum melakukan `ssh-add` harus menjalankan command `ssh-agent`. Sebelumnya saya sudah menjalankan command tersebut.

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
Security Group kedua Instance: All Traffic & MYSQL (3306)
Subnet kedua Instance: Memakai Subnet Private sebelumnya.
Kedua Instance memakai Key-Pair yang sama, JouzieAuliaRezky.pem
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
