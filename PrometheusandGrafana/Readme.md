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

```text docker-monitoring/ ├── docker-compose.yml └── prometheus/ └── prometheus.yml ```


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
