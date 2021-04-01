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

22. Menjalankan NPM untuk menjalankan `wayshub-frontend`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-33-01-338.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-33-06-972.jpg)

23. Konek alamat 192.168.0.20:3000 di browser

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%201/img/bandicam%202021-04-01%2004-38-01-222.jpg)

 
