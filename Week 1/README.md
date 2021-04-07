# Task Dev Ops
Jouzie Aulia Rezky - DWDS04JAR

Week 1

# VMware Local untuk deploy `wayshub-project`
Tools yang saya gunakan: Bash Windows Subsystem Linux, VMware Player, ISO Ubuntu Server 20.04. NodeSource (Node.JS 14x).

# - VMware - Install Ubuntu

Untuk Setup Network, bersamaan disaat instal Ubuntu ini.

1. Pilih `Create a New Virtual Machine`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-40-28-114.jpg)

2. Mengatur pengguna untuk login server

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-40-56-807.jpg)

3. Mengarahkan lokasi ISO Ubuntu yang saya ingin gunakan `ubuntu-20.04.2-live-server-amd64.iso`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-40-59-072.jpg)

4. Mengatur kapasitas penyimpanan sebesar 8GB

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-41-04-786.jpg)

5. Melakukan kostumasi Hardware di VM. Saya meng-kostumasi hardware VM dengan:

- RAM: 1GB
- Prosesor 2 Cores
- Bridge Connection dengan meng-configure sedikit di bagian adapter, untuk Wi-Fi Atheros saya.
- Display Resolusi 800x600

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-41-09-475.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-41-34-122.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-41-37-295.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-41-41-042.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-41-44-983.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-42-00-343.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-42-18-568.jpg)

6. Masuk Instalasi, Memilih English USA sebagai bahasa default.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-43-19-674.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-43-53-375.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-44-01-443.jpg)

# VMware - Setup Network

7. Mengatur IP Static

- Subnet 192.168.0.0/24 (255.255.255.0)
- Adreess: 192.168.0.20
- Gateway: 192.168.0.1
- Name Servers: 192.168.0.1

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-57-02-042.jpg)

8. Tidak meng-konfigurasi proxy, skip...

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-58-35-073.jpg)

9. Configure Ubuntu archive mirror sebagai default

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-58-38-776.jpg)

# Continue: VMware - Install Ubuntu

10. Melakukan kostumisasi penyimpanan server.

- Mount Boot `/` sebesar 6+GB dengan type `ext4`
- Mount Swab sebesar 1GB dengan type `swap`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2003-58-48-537.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-00-28-908.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-00-46-733.jpg)

11. Mengatur informasi user

- Nama: Jouzie Aulia Rezky
- Server Name: DWDS04JAR
- Username: aureezz
- Password: **********

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-01-56-571.jpg)

12. Install OpenSSH server agar dapat diremote.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-04-01-761.jpg)

13. Tidak menginstall Featured Server Snaps, karena tidak butuh.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-04-09-294.jpg)

14. Instalasi....

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-04-18-995.jpg)

15. Instalasi Selesai

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-13-51-472.jpg)

16. Proses Reboot, dan login server

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-18-04-621.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-21-35-595.jpg)

# VMware - Install Application

17. Melakukan remote SSH dari luar VM, dengan menggunakan Bash Windows Subsystem Linux (Ubuntu 20.04 Focal Fossa)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-22-12-056.jpg)

18. Melakukan update dan upgrade depedensi `sudo apt update` dan `sudo apt upgrade`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-23-39-507.jpg)

19. Instal NodeSource menggunakan curl (Node.js v14.x)

```
curl -fsSL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt-get install -y nodejs
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-26-44-672.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-27-13-244.jpg)

20. Melakukan clone project `wayshub-frontend`

```
git clone https://github.com/sgnd/wayshub-frontend
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-29-29-861.jpg)

21. Installasi NPM

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-29-48-970.jpg)

22. Menjalankan NPM dengan cara `npm start` untuk menjalankan `wayshub-frontend`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-33-01-338.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-33-06-972.jpg)

23. Konek alamat 192.168.0.20:3000 di browser

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-38-01-222.jpg)

 
# AWS - Create And Setup Server

# Membuat server Public Reverse Proxy

1. Launch Instance

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-42-59-759.jpg)

2. Sesuai task yang diminta, install Ubuntu 18.xx (18.04 LTS)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-43-14-555.jpg)

3. Memilih spesifikasi `t2.micro` sesuai dengan task.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-43-30-467.jpg)

4. Cukup merubah `Auto-assign Public IP` menjadi `Disable`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-44-11-382.jpg)

5. Storage server 8GB

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-45-14-601.jpg)

6. Configure Security Group, Tambah 3 Rules

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-46-35-775.jpg)

7. Review and Launch...

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-48-32-426.jpg)

8. Membuat Key Pair baru untuk akses instance pertama kali, `Create a new key pair` lalu isi Nama Keynya. Setelah itu Download

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-49-06-083.jpg)

9. Jika sudah, `View Instance`, lalu masuk ke ke `Elastic IP`, di sidebar kiri di menu `Network and Security`

Lalu klik `Allocate Elastic IP Adreess`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-50-08-409.jpg)

10. Klik Allocate 

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-50-22-386.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-50-20-060.jpg)

11. Selanjutnya, klik `Action` lalu `Associate Elastic IP Adreess` untuk melakukan Asosiasi Elastik IP dengan Instance Server Public yang sebelumnya dibuat

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-50-46-090.jpg)

12. Pilih Instance sebelumnya untuk diasosiasikan Elastic IP-nya, Lalu klik `Associate`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-50-53-632.jpg)

Pembuatan Instance Server Public selesai.

# Membuat server Private Aplikasi (wayshub-frontend)

1. Masih sama dengan sebelumnya, langkah pertama adalah `Launch Instance`, lalu pilih OS Ubuntu 18.xx

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-52-18-245.jpg)

2. Memilih Spesifikasi Server, pilih `t2.micro` Sesuai task

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-52-26-152.jpg)

3. Cukup merubah `Auto-assign Public IP` menjadi `Disable`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-52-36-290.jpg)

4. Add Storage sama seperti sebelumnya, hanya `8GB`.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-52-41-062.jpg)

5. Meng-konfigurasi Security Group, hanya saja ini berbeda seperti Server Public sebelumnya, yaitu hanya 1 type saja, yaitu `All Traffic` agar semua port dapat diakses.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-53-48-315.jpg)

6. Launch Instance....

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-54-14-299.jpg)

7. Memakai Key-Pair yang sebelum nya dibuat, agar dapat ditransfer dari Server Public, Jika sudah, Klik Launch Instance

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-55-04-660.jpg)

Pembuatan Instance Server Private selesai. Selanjutnya melalukan sedikit perubahan terhadap Subnet di 2 Instance

# Melakukan sedikit perubahan Subnet

1. Menuju `Services > VPC`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-13-40-666.jpg)

2. Klik Subnet, lalu rename yang semula `-` menjadi Subnet Public `subnet-c3ccf58e` dan Subnet Private `subnet-400eb371`. Cara mengetahui Itu subnet Public/Private atau bukan, cek kembali di `Instance > Pilih Instance nya > Klik Network > Cari Subnet ID`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-23-39-433.jpg)

Selanjutnya mengatur NAT INSTANCE terhadap Server Private.

# Konfigurasi NAT INSTANCE 

Karena sifat Server Private itu tidak ada IP Publicnya, maka dari itu Server Private tidak ada koneksi internet secara langsung. Maka dari itu perlu Meng-Konfigurasi NAT INSTANCE Agar Server Private dapat saluran koneksi Internet dari Server Public (54.162.149.199) dengan cara instalasi Instance Baru dengan menggunakan AMI (Amazon Machine Image) NAT 

1. Launch Instance > Community AMI > Ketik di search `nat`. Pilih versi teratas

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-24-53-709.jpg)

2. Memilih `t2.micro`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-25-28-478.jpg)

3. Di step ini, yang perlu dirubah hanyalah Subnet, lalu diarahkan di Subnet Public yang sebelumnya dibuat. Lalu `Auto-assigned Public IP` menjadi Enable

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-25-59-392.jpg)

4. Buat Security Group Baru, dengan 1 Rule saja, yaitu All Traffic, lalu isi Source nya menyesuaikan IP Subnet Private Sebelumnya. Cara mengecek IP nya, Subnet > Private Subnet nya > Network > IPv4 CDR. Saya mengisi Source `172.31.48.0/20`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-31-24-461.jpg)

5. Memilih Rekomendasi dari AWS

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-31-59-508.jpg)

6. Launch Instance...

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-32-04-607.jpg)

7. Masih tetap menggunakan Key-Pair yang sama

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-32-25-339.jpg)

8. Halaman akan diarahkan ke List Instance, Klik NAT INSTANCE yang sebelumnya dibuat, lalu klik `Action` lalu `Networking > Change Source/destination check`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-33-34-069.jpg)

9. Checklist pada kotak `STOP`, lalu save.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-33-44-376.jpg)

10. Masuk kembali ke `Services > Route Tables` dan lakukan `Create Route Tables`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-34-29-575.jpg)

11. Membuat Route baru, lalu pilih VPCnya, karena cuma 1, saya memilih yang itu saja.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-35-19-517.jpg)

12. Jika sudah, tampilan akan menjadi seperti ini. Klik Close.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-35-34-958.jpg)

13. Masih di Route Tables, Klik Route yang sebelumnya dibuat, lalu klik `Edit Routes`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-35-57-410.jpg)

14. Mengisi Destination `0.0.0.0/0` lalu arahakan Target ke NAT INSTANCE (dengan cara mengetik 'i-...' nanti akan keliatan NAT INSTANCE nya), jika sudah. Save.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-36-40-296.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-37-16-408.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-37-20-180.jpg)

15. Menuju Subnet, klik Subnet Private yang sebelumnya dibuat, Lalu Klik `Action > Edit Route Table Association`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/1.png)

16. Arahkan Route Table ID menuju Private Route yang sebelumnya dibuat di Route Tables, jika sudah. Save

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/2.png)

17. Subnet Private untuk Server Private sudah berhasil di asosiasikan, dan Installasi NAT INSTANCE juga sudah selesai.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/3.png)

Selanjutnya, Eksekusi Server Public Dan Private di Terminal

# Eksekusi server di Terminal

# Public Server

1. Masuk ke directory Downloads, lalu ubah perizinan terhadap file `.pem` dengan akses Superuser yang sebelumnya di download dengan `sudo chmod 400 JouzieAuliaRezky.pem`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-58-27-979.jpg)

2. Masuk ke Server Public yang sudah di asosiasikan dengan Elastic IP (54.162.149.199) dengan akses Superuser dengan cara `sudo ssh -i JouzieAuliaRezky.pem ubuntu@54.162.149.199`. Lalu ketik `yes`.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2022-59-44-616.jpg)

3. Melakukan penambahan user dengan metode `adduser`, agar nanti Login Server Public tidak menggunakan Key-Pair lagi, dengan cara `sudo adduser jouzie`, Lalu mengisi value User Information, tekan `ENTER` Jika tidak ingin di-isikan, jika sudah ketik `Y`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-00-32-824.jpg)

4. Melakukan usermod `sudo usermod -aG sudo jouzie`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-00-54-454.jpg)

5. Masuk ke directory `ssh` dengan cara `cd /etc/ssh/` lalu merubah konfigurasi SSHD dengan menggunakan nano `sudo nano sshd_config`. Cari pada bagian `PasswordAuthentication`, mengganti yang sebelumnya `no` menjadi `yes` agar dapat login menggunakan user yang sebelumnya. Jika sudah, save dengan cara `CTRL-X` lalu Save Overwrite ketik `Y`.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-01-35-762.jpg)

6. Melakukan restart terhadap SSDH dengan cara `sudo systemctl restart sshd`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-02-29-025.jpg)

7. Ketik `exit` untuk keluar dari server, untuk mencoba login dengan user yang sebelumnya dibuat, dengan cara `ssh jouzie@54.162.149.199`, Memasukan Password, dan berhasil. Jika sudah, `Exit` Untuk keluar, langkah berikutnya Meng-Transfer Key-Pair yang sebelumnya.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-02-49-645.jpg)

# Private Server

8. Melakukan transfer (upload) Key-Pair dari local ke Server Public (54.162.149.199) dengan cara `scp JouzieAuliaRezky.pem jouzie@54.162.149.199:/home/JouzieAuliaRezky.pem` (FORMAT `scp NamaKey.pem user@ip:/direktori_untuk_menyimpan/Nama-Key.pem`) lalu masukan Password User.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-10-10-018.jpg)

9. Login Server Public, lalu mengecek apakah file Key-Pair nya sudah terupload apa belum. Jika sudah, saya melakukan Perubahan Perizinan terhadap `JouzieAuliaRezky.pem` dengan cara `chmod 600 JouzieAuliaRezky.pem`, lalu Masuk ke Server Private menggunakan Key-Pair dengan cara `ssh -i JouzieAuliaRezky.pem ubuntu@172.31.48.93`, ketik `YES` untuk melakukan validasi Fingerprint. Cara mengecek IP Private nya, masuk ke AWS Management Console, klik Instance Server Private yang sudah dibuat sebelumnya, lalu cari `Private IPv4 addresses`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-11-30-137.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-12-38-399.jpg)

10. Melakukan PING dari Server Private ke `8.8.8.8`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-39-45-382.jpg)
