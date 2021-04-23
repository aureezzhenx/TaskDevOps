# Task Dev Ops
Jouzie Aulia Rezky - DWDS04JAR

Week 3 - Docker & CI/CD

- [Setup Monitoring Server](https://github.com/aureezzhenx/TaskDevOps/tree/main/Week%204#setup-monitoring-server)
- Connect Multiple Server to Prometheus
- Deploy PHP Application in cPanel
- Setup Server with Ansible

# Setup Monitoring Server

1. Akses `awseducate.com` Lalu buat Instance Private baru untuk Monitoring ini. Kemudian buatlah `adduser` agar tidak menggunakan Key-Pair lagi.

```
1. sudo adduser jouziemonitoring
2. Mengisi identitas user
3. sudo usermod -aG sudo jouziemonitoring
4. Melakukan perubahan PasswordAuthentication di sshd_config
5. sudo nano /etc/ssh/sshd_config
6. Rubah PasswordAuthentication dari NO menjadi YES
7. Save Overwrite
8. Restart sshd
9. sudo systemctl restart sshd
```

2. Akses kembali ke Instance tersebut tanpa Key-Pair.

3. Memulai Instalasi (Install Prometheus, Node Docker, menambah user prometheus dan node_exporter, membuat service dan systemd untuk prometheus dan node_exporter)

```
1. Membuat user untuk prometheus dan node_exporter.

sudo useradd --no-create-home --shell /bin/false prometheus
sudo useradd --no-create-home --shell /bin/false node_exporter

2. Membuat folder prometheus.

sudo mkdir /etc/prometheus
sudo mkdir /var/lib/prometheus

3. Set user dan group ownership folder.

sudo chown prometheus:prometheus /etc/prometheus
sudo chown prometheus:prometheus /var/lib/prometheus

4. Download Prometheus

curl -LO https://github.com/prometheus/prometheus/releases/download/v2.17.1/prometheus-2.17.1.linux-amd64.tar.gz
tar xzvf prometheus-2.17.1.linux-amd64.tar.gz 

5. Copy folder prometheus dan promtool.

sudo cp prometheus-2.17.1.linux-amd64/prometheus /usr/local/bin
sudo cp prometheus-2.17.1.linux-amd64/promtool /usr/local/bin

6. Set user dan group ownership untuk prometheus dan promtool.

sudo chown prometheus:prometheus /usr/local/bin/prometheus
sudo chown prometheus:prometheus /usr/local/bin/promtool

7. Copy folder consoles dan console_libraries.

sudo cp -r prometheus-2.17.1.linux-amd64/consoles /etc/prometheus
sudo cp -r prometheus-2.17.1.linux-amd64/console_libraries /etc/prometheus

8. Set user dan group ownership folder consoles dan console_libraries.

sudo chown -R prometheus:prometheus /etc/prometheus/consoles
sudo chown -R prometheus:prometheus /etc/prometheus/console_libraries

9. Konfigurasi Promotheus, membuat file konfigurasi untuk prometheus.

sudo nano /etc/prometheus/prometheus.yml

Isi seperti ini:

global:
  scrape_interval: 15s
scrape_configs:
  - job_name: 'prometheus'
    scrape_interval: 5s
    static_configs:
      - targets: ['localhost:9090']    

10. Set user dan group ownership prometheus.yml

sudo chown prometheus:prometheus /etc/prometheus/prometheus.yml

11. Membuat service untuk prometheus.

sudo nano /etc/systemd/system/prometheus.service

Isi seperti ini:

[Unit]
Description=Prometheus
Wants=network-online.target
After=network-online.target

[Service]
User=prometheus
Group=prometheus
Type=simple
ExecStart=/usr/local/bin/prometheus \
    --config.file /etc/prometheus/prometheus.yml \
    --storage.tsdb.path /var/lib/prometheus/ \
    --web.console.templates=/etc/prometheus/consoles \
    --web.console.libraries=/etc/prometheus/console_libraries

[Install]
WantedBy=multi-user.target

12. Aktifkan prometheus service.

sudo systemctl daemon-reload
sudo systemctl enable prometheus
sudo systemctl start prometheus
sudo systemctl status prometheus

13. Download dan extract Node Exporter.

curl -LO https://github.com/prometheus/node_exporter/releases/download/v0.18.1/node_exporter-0.18.1.linux-amd64.tar.gz
tar xzvf node_exporter-0.18.1.linux-amd64.tar.gz

14. Copy node_exporter. Set user dan group ownership node_exporter.

cp node_exporter-0.18.1.linux-amd64/node_exporter /usr/local/bin
chown node_exporter:node_exporter /usr/local/bin/node_exporter

15. Membuat service untuk node_exporter.

sudo nano /etc/systemd/system/node_exporter.service

Isi seperti ini:

[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=multi-user.target

16. Aktifkan node_exporter service.

sudo systemctl daemon-reload
sudo systemctl enable node_exporter
sudo systemctl start node_exporter
sudo systemctl status node_exporter

17. Konfigurasi Prometheus untuk Node Exporter, menambahkan node_exporter di konfigurasi prometheus.yml

sudo nano /etc/prometheus/prometheus.yml

Edit konfigurasi prometheus.yml seperti ini:

global:
  scrape_interval: 15s
scrape_configs:
  - job_name: 'prometheus'
    scrape_interval: 5s
    static_configs:
      - targets: ['localhost:9090']
  - job_name: 'node_exporter'
    scrape_interval: 5s
    static_configs:
      - targets: ['localhost:9100']

18. Restart prometheus.

sudo systemctl restart prometheus
sudo systemctl status prometheus
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2001-42-11-930.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2001-42-17-005.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2002-11-49-768.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2001-42-30-193.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2002-12-52-875.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2001-42-39-859.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2002-13-05-953.jpg)

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2001-45-44-394.jpg)

4. Melakukan test akses Web Node Exporter dan Prometheus

Catatan:

```
Saya melakukan test akses ini dengan menggunakan VPN dari REVERSE PROXY / GATEWAY dengan OPENVPN, dan saya juga sudah menambahkan domain record untuk IP Private ini untuk semua Instance Private saya.

serverfrontend.jouzie.onlinecamp.id
serverbackend.jouzie.onlinecamp.id
serverdatabase.jouzie.onlinecamp.id
servercicd.jouzie.onlinecamp.id
servermonitoring.jouzie.onlinecamp.id
```

Akses `localhost:9100` untuk mengecek Web Node Exporter

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2001-46-29-351.jpg)

Akses `localhost:9090` untuk mengecek Web Prometheus

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2001-46-44-131.jpg)

Mengecek status Node Exporter dan Prometheus berjalan dengan baik / tidak

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2001-46-47-712.jpg)

5. Melakukan Reverse Proxy untuk Prometheus

Membuat DNS Record baru untuk Prometheus di `dash.cloudflare.com`

Catatan:

```
Type Record: A
Nama: monitoring.jouzie.onlinecamp.id
IPv4 Address: 34.232.133.218
TTL: Auto
Proxy status: DNS Only
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2023-34-30-605.jpg)

6. Masuk ke Instance `REVERSE PROXY GATEWAY - PUBLIC` untuk melakukan Reverse Proxy terhadap aplikasi Prometheus yang terinstall di servernya.

Membuat konfigurasi baru `monitoring.conf` di direktori `/etc/nginx/monitoring`. Membuat direktori baru dengan hak akses root. `sudo mkdir /etc/nginx/monitoring/`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2023-37-00-338.jpg)

7. Edit konfigurasi `monitoring.conf` dengan hak akses root. Edit seperti ini:

```
server
{
      server_name monitoring.jouzie.onlinecamp.id;
  
      location /
      {
          proxy_pass http://servermonitoring.jouzie.onlinecamp.id:9090:
      }
}
```

Jika sudah, save overwrite

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2023-38-16-284.jpg)

8. Edit konfigurasi `nginx.conf` agar `monitoring.conf` sebelumnya dapat dieksekusi. 

```
include /etc/nginx/monitoring/*;
```

Jika sudah, save overwrite

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2023-38-55-910.jpg)

9. Restart `nginx` dengan command `sudo nginx -t` dan `sudo systemctl restart nginx` agar konfigurasi sebelumnya yang ditambahkan dapat dijalankan.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2023-39-19-009.jpg)

10. Jalankan command ini untuk mendaftarkan SSL Certificate terhadap subdomain `monitoring.jouzie.onlinecamp.id` yang sebelumnya sudah dibuat. 

```
sudo certbot certonly --dns-cloudflare --dns-cloudflare-credentials ~/.secrets/cloudflare.ini -d monitoring.jouzie.onlinecamp.id
```

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2023-40-18-765.jpg)

11. Jalankan command `sudo certbot` kembali untuk melakukan redirect ke HTTPS dan mengatur renewal SSL Certificate. Pilih urutan yang sesuai.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2023-40-52-973.jpg)

12. Kembali mengecek konfigurasi `monitoring.conf` apakah SSL dan HTTPS Redirect sudah terpasang atau belum dengan command `sudo cat /etc/nginx/monitoring/monitoring.conf`

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2023-41-44-107.jpg)

13. Subdomain `monitoring.jouzie.onlinecamp.id` sudah berhasil di Reverse Proxy dari Gateway, dan sudah terpasang SSL dari Let's Encrypt.

![alt text](https://github.com/aureezzhenx/TaskDevOps/blob/main/Week%204/img1/bandicam%202021-04-23%2023-43-06-389.jpg)































