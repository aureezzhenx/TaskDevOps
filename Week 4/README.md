# Task Dev Ops
Jouzie Aulia Rezky - DWDS04JAR

Week 3 - Docker & CI/CD

- Setup Monitoring Server
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
      - targets: ['45.77.252.94:9090']
  - job_name: 'node_exporter'
    scrape_interval: 5s
    static_configs:
      - targets: ['45.77.252.94:9100']

18. Restart prometheus.

sudo systemctl restart prometheus
sudo systemctl status prometheus
```











