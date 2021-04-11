# Task Dev Ops
Jouzie Aulia Rezky - DWDS04JAR

Week 1
- [VMware - Install Ubuntu](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/README.md#--vmware---install-ubuntu)
- [VMware - Setup Network](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/README.md#vmware---setup-network)
- [VMware - Server For Application](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/README.md#vmware---install-application)
- [AWS - Create And Setup Server](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/README.md#aws---create-and-setup-server)
- [AWS - Server For Application](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/README.md#aws---server-for-application)
- [AWS - Reverse Proxy](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/README.md#aws---reverse-proxy)
- [AWS - Custom Domain](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/README.md#aws---custom-domain)
- [AWS - SSL Configuration](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/README.md#aws---ssl-configuration)

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

20. Melakukan clone project `wayshub-frontend` dengan command berikut:

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

10. Melakukan PING dari Server Private ke `8.8.8.8` dan `google.com`. Intenet sudah dapat digunakan.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-39-45-382.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-41-10-065.jpg)

11. Sama seperti sebelumnya, saya melakukan penambahan user agar login Server Private tidak menggunakan Key-Pair nya lagi. `sudo adduser jouziefrontend`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-56-07-028.jpg)

12. Melakukan `sudo usermod -aG sudo jouziefrontend`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-56-28-132.jpg)

13. Konfigurasi SSHD Config, dengan cara `sudo nano /etc/ssh/sshd_config`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-56-58-263.jpg)

14. Melakukan Perubahan terhadap `PasswordAuthentication` Menjadi `YES`. Sama seperti sebelumnya di Server Public.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-57-15-296.jpg)

15. Jika sudah, merestart SSHD untuk merefresh config yang sudah diatur sebelumnya dengan cara `sudo systemctl restart sshd`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-57-41-679.jpg)

16. Jika sudah, ketik `exit` untuk keluar dari server Private menuju Server Public, untuk mencoba login Server Private dengan user `jouziefrontend`, Login Server Private kembali dari Server Public dengan cara `ssh jouziefrontend@172.31.48.93`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-06%2023-58-23-048.jpg)

# AWS - Server For Application

1. Login dari Server Public ke Server Private (172.31.48.93) `ssh jouziefrontend@172.31.48.93`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-02-45-776.jpg)

2. Melakukan update depedensi di server Private. `sudo apt upgrade` dan `sudo apt update`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-04-22-014.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-04-33-537.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-05-15-822.jpg)

3. Meng-instal `Node Version Manager (NVM)` dengan command `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash`. lalu ketik `exec bash` dan ketik `nvm -v` agar memastikan NVM telah terinstall

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-09-16-217.jpg)

4. Meng-Install Node.js 14 dengan NVM dengna cara `nvm install 14`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-09-35-082.jpg)

5. Memastikan Node.js telah terinstall, ketik `node -v` dan `npm -v`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-10-08-232.jpg)

6. Melakukan Clone git `wayshub-frontend`

```
git clone https://github.com/sgnd/wayshub-frontend
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-10-23-131.jpg)

7. Masuk ke directory `wayshub-frontend` dengan cara `cd wayshub-frontend/` lalu install package nya dengan cara `npm install`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-10-52-014.jpg)

8. Instal `pm2` di directory Wayshub agar aplikasinya berjalan di background

```
cd wayshub-frontend/
npm install pm2 -g
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-15-35-218.jpg)

9. Masih di directory Wayshub, ketik `pm2 ecosystem` untuk meng-generate file `ecosystem.config.js` didalam folder `wayshub-frontend`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-15-58-713.jpg)

10. Masih di directory Wayshub, melakukan konfigurasi file `ecosystem.config.js` dengan `sudo nano ecosystem.config.js` seperti ini

```
module.exports=
{
      apps:
      [
                {
                         name: 'wayshub';
                         script: 'npm';
                         args: 'start';
                }
      ]
}
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-20-02-118.jpg)

11. Masih di directory Wayshub, menjalankan `pm2` dengan cara `pm2 start ecosystem.config.js`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-21-07-844.jpg)

12. Meng-inisialisasi `pm2` dengan Key-Metrics yang disedesiakan di `https://app.pm2.io/` agar dapat memantau `pm2 wayshub` tanpa perlu login server Private, Saya login menggunakan akun Google.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2018-38-31-154.jpg)

13. Memberi nama bucket baru, saya memberi nama dengan `Wayshub-Frontend`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2018-39-54-475.jpg)

14. Menghubungkan `pm2` ke `Website pm2.io` dengan cara copy link-nya. Lalu paste command nya dengan cara masuk ke directory `wayshub-frontend` di server Private.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2018-40-18-277.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2018-41-53-814.jpg)

15. `pm2 wayshub` sudah terkoneksi di Key-Matrics milik pm2.io. Agar dapat memonitoring tanpa perlu login server Private. 

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2018-42-30-985.jpg)

# AWS - Reverse Proxy

1. Login ke Server Public `ssh jouzie@54.162.149.199` 

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-25-39-057.jpg)

2. Melakukan update depedensi dengan cara `sudo apt upgrade` dan `sudo apt update`, ketik `Y` untuk konfirmasi.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-26-12-545.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-29-39-250.jpg)

3. Selanjutnya, install NGINX dengan command `sudo apt install nginx`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-31-39-145.jpg)

4. Membuat direktori `wayshub` di `/etc/nginx` dengan command `sudo mkdir /etc/nginx/wayshub`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-32-20-029.jpg)

5. Jika sudah, membuat dan mengedit file `frontend.conf` dengan nano. Command `sudo nano frontend.conf`. Lalu edit seperti ini

```
server
{
         listen 80;
         
         server_name 54.162.149.199;
         
         location / 
         {
                proxy_pass http://172.31.48.93:3000;
         }
}
```

Jika sudah, Pencet `CTRL+X` untuk save, lalu save dengan file `frontend.conf`, Ketik `Y`.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-36-50-938.jpg)

6. Pindah ke directory `/etc/nginx/`. Lalu edit `nginx.conf` dengan nano. Command `sudo nano nginx.conf`. Cari pada bagian include, lalu tambahkan seperti ini.

```
include /etc/nginx/wayshub/*;
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-37-51-313.jpg)

7. Jika sudah, lakukan validasi konfigurasi nginx dengan command `sudo nginx -t`. Jika sudah lakukan refresh konfigurasi dengan cara Merestart nginx-nya dengan command `sudo systemctl restart nginx`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-38-27-167.jpg)

8. Buka browser. Akses `59.162.149.199` tanpa port `3000`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-38-57-915.jpg)

# AWS - Custom Domain

1. Akses `dash.cloudflare.com` Lalu pilih akun `Sugandaletters@outlook.com's Account`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-40-59-808.jpg)

2. Klik `onlinecamp.id`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-41-04-288.jpg)

3. Membuat record Subdomain baru, Klik `Add record` lalu pilih type `A` lalu isi di bagian name `jouzie` sebagai subdomain nya, mengisi `IPv4 adreess` dengan IP Server Public atau Reverse Proxy `54.162.149.199` dan Proxy On. Lalu save.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-41-47-607.jpg)

4. Login ke Server Public `ssh jouzie@59.162.149.199`. lalu buat folder `.secrets`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-43-27-227.jpg)

5. Membuat dan mengedit file `cloudflare.ini` di folder `.secrets` sebelumnya dengan command `sudo nano .secrets/cloudflade.ini `

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-44-04-171.jpg)

6. Sebelum mengedit file `cloudflare.ini`, masuk ke profile Cloudflare pribadi (jouzie.aurez@gmail.com), Lalu klik View di Global API Key.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-42-18-508.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-42-38-765.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-44-57-726.jpg)

7. Masuk ke edit nano `cloudflare.ini` lalu isi email dan Global API Key yang sebelumnya didapat dari Cloudflare seperti ini:

```
dns_cloudflare_email = "jouzie.aurez@gmail.com"
dns_cloudflare_api_key = "9721bb68b9e97ed6dda38c271f6a06069d422"
```

Jika sudah, Save dengan cara pencet `CTRL+X` lalu save dengan nama file overwrite `cloudflare.ini`, ketik `Y`.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-45-28-663.jpg)

8. Melakukan perubahan perizinan terhadap directory `.secrets` dan file `cloudflare.ini`

```
sudo chmod 0700 .secrets
sudo chmod 0400 .secrets/cloudflare.ini
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-48-23-321.jpg)

9. Menginstall `certbot` dengan 3 command berikut:

```
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo apt-get install certbot python3-certbot-nginx python3-certbot-dns-cloudflare
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-50-52-718.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-51-00-429.jpg)

10. Menjalankan `certbot` dengan Cloudflare Authenticator dengan command:

```
sudo certbot certonly --dns-cloudflare --dns-cloudflare-credentials ~/.secrets/cloudflare.ini -d jouzie.onlinecamp.id challenges dns-01
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-52-31-557.jpg)

11. Mengisi alamat email yang terdaftar di Cloudflare, dan setuju atas Terms & Services Lets Encrypt, dan tunggu verifikasi nya selama kurang lebih 10 detik.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-52-50-470.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2000-53-10-974.jpg)

12. Jika sudah, masuk ke directory `/etc/nginx/wayshub/` dengan command `cd /etc/nginx/wayshub` lalu edit file `frontend.conf` nya dengan nano, command `sudo nano frontend.conf`. Edit seperti ini

```
server
{
         listen 80;
         
         server_name jouzie.onlinecamp.id;
         
         location / 
         {
                proxy_pass http://172.31.48.93:3000;
         }
}
```

Hanya merubah server_name. Jika sudah, Save dengan `CTRL+X` lalu save overwrite `frontend.conf` ketik `Y`.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2001-01-42-452.jpg)

13. Jika sudah, lakukan validasi konfigurasi nginx dengan command `sudo nginx -t`. Jika sudah lakukan refresh konfigurasi dengan cara Merestart nginx-nya dengan command `sudo systemctl restart nginx`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2001-02-21-118.jpg)

14. Buka Browser. Akses `jouzie.onlinecamp.id` 

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2001-02-41-183.jpg)

# AWS - SSL Configuration

1. Masih di Server Public, ketik command `sudo certbot` Lalu ketik `1` sesuai urutan subdomain saya

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2001-03-27-577.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2001-03-32-338.jpg)

2. Memilih Attempt to reinstall this existing certificate, ketik `1`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2001-03-38-648.jpg)

3. Melakukan redirect dari HTTP menuju HTTPS, ketik `2`. Dan Sertifikat Lets Encrypt! telah selesai dipasang

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2001-04-18-678.jpg)

4. Mengecek `frontend.conf` di `/etc/nginx/wayshub` yang sudah di generate oleh certbot. Command `sudo nano frontend.conf`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2001-05-03-818.jpg)

5. Melakukan Restart nginx dengan command `sudo systemctl reload nginx` 

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2001-05-32-396.jpg)

6. Akses `jouzie.onlinecamp.id` lalu cek Sertifikat Lets Encrypt!

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-07%2001-06-38-203.jpg)
