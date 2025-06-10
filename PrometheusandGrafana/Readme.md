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

### 1. Clone the repo

```bash
git clone https://github.com/your-username/docker-monitoring-stack.git
cd docker-monitoring-stack
