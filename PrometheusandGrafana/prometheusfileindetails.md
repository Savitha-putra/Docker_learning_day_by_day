Full prometheus.yml (Recap)
```yaml
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
🔍 Line-by-Line Breakdown
✅ global: section
```yaml
global:
  scrape_interval: 15s
```
scrape_interval: How often Prometheus collects metrics (default is 1m, here it's 15s).
This means every 15 seconds, Prometheus checks all configured targets for new data.

📦 scrape_configs: section
This is where you define what services Prometheus should monitor, and how.

Each entry under scrape_configs is called a job.

🧪 Job #1: Prometheus monitoring itself
```yaml
- job_name: 'prometheus'
  static_configs:
    - targets: ['prometheus:9090']
```
job_name: A label to organize this group of targets.

static_configs: Defines a static list of target endpoints.

targets: Services Prometheus should scrape (in this case, itself).

Prometheus exposes its own metrics at /metrics on port 9090.

🌡️ Job #2: Node Exporter (Host Metrics)
```yaml
- job_name: 'node-exporter'
  static_configs:
    - targets: ['node-exporter:9100']
```
Job name: Identifies this as a host metrics collector.

Target: The Node Exporter container running on port 9100.

This job collects OS-level and container-level metrics like:

CPU usage

Memory consumption

Disk I/O

Network stats

Docker container details (via cgroups)

⚠️ Notes on Service Discovery
Prometheus resolves these target names (prometheus, node-exporter) by Docker container name, thanks to Docker Compose networking.

If you were not using Docker Compose, you'd need actual IPs or localhost.

✅ Summary Table
Field	Purpose
scrape_interval	Global frequency for scraping targets
job_name	Label to group a set of targets
targets	Services to scrape metrics from

Next to learn
👀 Want More?
You can extend this file later to:

Scrape a custom app like Python/Node/Java

Use relabel_configs to filter labels

Discover targets dynamically (e.g., via Kubernetes service discovery)

Add alerting rules using rule_files

Would you like an example of how to expose custom metrics from a Python or Node.js app and let Prometheus scrape that too?

