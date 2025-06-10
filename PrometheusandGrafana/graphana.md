# 📊 Grafana Overview

**Grafana** is an open-source analytics and visualization platform. It allows you to query, visualize, alert on, and explore your metrics data no matter where it's stored — Prometheus, Loki, Elasticsearch, InfluxDB, and many more.

---

## 🔍 Why Use Grafana?

Grafana is built for observability and monitoring. It excels in:

- **Visualizing time-series data** from multiple sources
- **Creating real-time, dynamic dashboards**
- **Setting up alerts** for threshold-based notifications
- Supporting a wide range of **data sources** (Prometheus, MySQL, PostgreSQL, etc.)
- Built-in **user authentication, team roles, and sharing**

---

## 🧠 Key Features

| Feature            | Description |
|--------------------|-------------|
| 📈 Dashboards       | Organize visualizations into interactive dashboards |
| 🛠 Panels           | Visual elements like graphs, tables, gauges |
| 📦 Plugins          | Add support for new data sources or panels |
| 📣 Alerting         | Trigger alerts on defined thresholds |
| 🔒 User Management  | Role-based access and SSO support |
| 🔗 Data Sources     | Supports over 30+ databases and services |

---

## 🚀 How Grafana Fits in Our Monitoring Stack

In this project, Grafana visualizes metrics collected by **Prometheus** and exposed by:

- **Prometheus itself** (target: `prometheus:9090`)
- **Node Exporter** (target: `node-exporter:9100`)
- Any other service exposing Prometheus-compatible metrics

---

## ⚙️ Accessing Grafana in Local Setup

If you followed the Docker Compose setup in this repo:

- URL: [http://localhost:3000](http://localhost:3000)
- Default Credentials:
  - Username: `admin`
  - Password: `admin`

---

## 🛠 Set Up Prometheus as a Data Source

1. Open Grafana at [http://localhost:3000](http://localhost:3000)
2. Go to **Settings → Data Sources**
3. Click **Add data source**
4. Choose **Prometheus**
5. Set URL to: `http://prometheus:9090`
6. Click **Save & Test**

---

## 📊 Import a Pre-Built Dashboard

To quickly see system metrics:

1. Go to **+ → Import**
2. Enter Dashboard ID: `1860`
3. Choose Prometheus as data source
4. Click **Import**

This loads a full **Node Exporter** dashboard with CPU, memory, disk, and network stats.

---

## 🔔 Alerting (Optional)

Grafana supports alerting with:

- Email
- Slack
- Webhooks
- Microsoft Teams

Set alert rules on panels to get notified when a metric crosses a threshold.

---

## 🔗 Useful Links

- [Grafana Docs](https://grafana.com/docs/)
- [Grafana Docker Hub](https://hub.docker.com/r/grafana/grafana)
- [Prometheus + Grafana Guide](https://grafana.com/docs/grafana/latest/datasources/prometheus/)
- [Node Exporter Dashboard (ID: 1860)](https://grafana.com/grafana/dashboards/1860)

---

## 🙌 Contribution

Feel free to add custom dashboards or configure new services in this setup — pull requests welcome!

