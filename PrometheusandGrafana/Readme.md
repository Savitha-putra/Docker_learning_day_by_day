# 🐳 Docker Monitoring Stack with Prometheus, Node Exporter & Grafana

This project sets up a complete local monitoring stack using **Docker Compose**, including:
- 3 sample app containers (`nginx`, `httpd`, `redis`)
- **Prometheus** for metrics collection
- **Node Exporter** for system & Docker metrics
- **Grafana** for beautiful visual dashboards

---

## 📦 Stack Overview

| Service       | Port      | Description                     |
|---------------|-----------|---------------------------------|
| App 1 (nginx) | `8081`    | Demo app                        |
| App 2 (httpd) | `8082`    | Demo app                        |
| App 3 (redis) | `6379`    | Redis container                 |
| Prometheus    | `9090`    | Metrics collection & PromQL UI |
| Node Exporter | `9100`    | System & container metrics      |
| Grafana       | `3000`    | Dashboards & visualization      |

---

## 🚀 Getting Started

### 1. directory structure

```text
docker-monitoring/ 
├── docker-compose.yml
└── prometheus
 └── prometheus.yml
 ```


### 2. docker-compose.yml

```bash
version: '3.8'

services:
  app1:
    image: nginx
    container_name: app1
    ports:
      - "8081:80"

  app2:
    image: httpd
    container_name: app2
    ports:
      - "8082:80"

  app3:
    image: redis
    container_name: app3
    ports:
      - "6379:6379"

  node-exporter:
    image: prom/node-exporter
    container_name: node-exporter
    ports:
      - "9100:9100"

  prometheus:
    image: prom/prometheus
    container_name: prometheus
    volumes:
      - ./prometheus/prometheus.yml:/etc/prometheus/prometheus.yml
    ports:
      - "9090:9090"

  grafana:
    image: grafana/grafana
    container_name: grafana
    ports:
      - "3000:3000"
    volumes:
      - grafana-storage:/var/lib/grafana

volumes:
  grafana-storage:

```

### 3. prometheus.yml 

``` bash
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['prometheus:9090']

  - job_name: 'node-exporter'
    static_configs:
      - targets: ['node-exporter:9100']
```

### 4. run docker compose command from /docker-monitoring where you have kept docker-compose.yml

``` bash
docker-compose up -d
```

### 5. current output of above docker compose 

```bash
[+] Running 8/8
 ✔ Network docker-monitoring_default           Created                                                                                                                                                       0.2s
 ✔ Volume "docker-monitoring_grafana-storage"  Created                                                                                                                                                       0.0s
 ✔ Container app1                              Started                                                                                                                                                       2.9s
 ✔ Container app3                              Started                                                                                                                                                       3.2s
 ✔ Container node-exporter                     Started                                                                                                                                                       3.2s
 ✔ Container prometheus                        Started                                                                                                                                                       3.2s
 ✔ Container app2                              Started                                                                                                                                                       2.9s
 ✔ Container grafana                           Started                                                                                                                                                       3.2s



dheeraj@Dheeraj-pc-best MINGW64 ~/docker-monitoring
$ docker ps
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS          PORTS                    NAMES
24cea78b903b   redis                "docker-entrypoint.s…"   15 minutes ago   Up 15 minutes   0.0.0.0:6379->6379/tcp   app3
ba2109113fd2   nginx                "/docker-entrypoint.…"   15 minutes ago   Up 15 minutes   0.0.0.0:8081->80/tcp     app1
6e40bb84d9da   httpd                "httpd-foreground"       15 minutes ago   Up 15 minutes   0.0.0.0:8082->80/tcp     app2
f1ca912c9d88   grafana/grafana      "/run.sh"                15 minutes ago   Up 15 minutes   0.0.0.0:3000->3000/tcp   grafana
f45f143eae3d   prom/prometheus      "/bin/prometheus --c…"   15 minutes ago   Up 15 minutes   0.0.0.0:9090->9090/tcp   prometheus
a7e86f1f3898   prom/node-exporter   "/bin/node_exporter"     15 minutes ago   Up 15 minutes   0.0.0.0:9100->9100/tcp   node-exporter
```

### 6. Open Prometheus and Grafana in browser

``` bash
| Tool       | URL                                            |
| ---------- | ---------------------------------------------- |
| Prometheus | [http://localhost:9090](http://localhost:9090) |
| Grafana    | [http://localhost:3000](http://localhost:3000) |
```

This is how prometheus looks like

![image](https://github.com/user-attachments/assets/2180141a-7539-492e-9a83-bd97046dca91)


This is how grafana looks like

![image](https://github.com/user-attachments/assets/994f8195-ba51-45f2-93ef-9800fcd762ca)


### 7. how to setup Grafana Dashbaord

``` bash
Open http://localhost:3000

Login: admin / admin → Set new password

Add Data Source:

Go to ⚙️ Settings → Data Sources → Add Data Source

Choose Prometheus

Set URL to: http://prometheus:9090

Click Save & Test

Import a Dashboard:

Click "+" → Import

Enter dashboard ID: 1860

Click Load, choose Prometheus as data source, click Import

🎉 You’ll now see full system metrics like CPU, memory, disk, and Docker info — thanks to Node Exporter.

```
