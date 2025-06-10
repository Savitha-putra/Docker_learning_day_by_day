✅ version: '3.8'
Specifies the Compose file format version.

Version 3.8 supports features like named volumes, configs, secrets, etc.

📦 services: block
Each service is a container managed by Docker Compose.

🧪 app1, app2, app3
These are 3 demo containers to simulate apps you might monitor.

Example: app1
```yaml
app1:
  image: nginx                # Official NGINX web server image
  container_name: app1        # Custom name for the container
  ports:
    - "8081:80"               # Host port 8081 maps to container port 80
```
image: Downloads and runs the latest nginx, httpd, and redis images.
container_name: Makes it easier to refer to the container manually.
ports: Maps local machine ports to container internal ports.

📡 node-exporter
```yaml
node-exporter:
  image: prom/node-exporter
  container_name: node-exporter
  ports:
    - "9100:9100"
```
This container exposes host system metrics (CPU, RAM, disk, network).
Prometheus will scrape this at port 9100.

📈 prometheus
```yaml
prometheus:
  image: prom/prometheus
  container_name: prometheus
  volumes:
    - ./prometheus/prometheus.yml:/etc/prometheus/prometheus.yml
  ports:
    - "9090:9090"
```
Image: Uses the official Prometheus server.
Volume: Mounts your custom config file to container's config path.
Port: Web UI available at http://localhost:9090.

The file prometheus.yml defines what metrics to scrape and from where.

📊 grafana
```yaml
grafana:
  image: grafana/grafana
  container_name: grafana
  ports:
    - "3000:3000"
  volumes:
    - grafana-storage:/var/lib/grafana
```
Image: Official Grafana dashboard.
Port: Web UI on http://localhost:3000.
Volume: Stores dashboards/configs persistently in a named volume.

💾 volumes: section
```yaml
volumes:
  grafana-storage:
```

Defines a named volume that persists Grafana's data even if the container is removed.
Keeps dashboards, settings, and plugins safe across restarts.

🎯 Bonus Tips
You can restart the stack anytime with:

```bash
docker-compose down
docker-compose up -d
```
If you want to see logs for any container:

```bash
docker logs prometheus
docker logs grafana
```
To enter a container:

```bash
docker exec -it app1 bash
```
