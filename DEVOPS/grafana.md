# 📊 Grafana Cheatsheet

> 🚀 Complete Grafana Guide for Beginners to Advanced Users  
> 📈 Learn Grafana Dashboards, Data Sources, Alerting, Loki, Plugins, Security & Monitoring

---

# 📚 Table of Contents

1. Introduction to Grafana  
2. Key Concepts  
3. Grafana Installation  
4. Configuring Data Sources  
5. Building Dashboards  
6. Grafana Alerting  
7. Grafana Plugins  
8. Dashboard Templating  
9. Customizing Grafana  
10. Securing Grafana  
11. Advanced Queries & Visualizations  
12. Grafana Loki  
13. Grafana in Kubernetes  
14. Troubleshooting Grafana  
15. References  

---

# 🚀 1. Introduction to Grafana

## 🔹 What is Grafana?

Grafana is an open-source platform for monitoring and observability that allows users to query, visualize, and alert on metrics from multiple data sources.

Grafana supports:

- Prometheus
- InfluxDB
- Elasticsearch
- Loki
- MySQL
- PostgreSQL

It helps teams:

- Monitor infrastructure
- Visualize metrics
- Analyze logs
- Configure alerts
- Improve observability

---

## 🔑 Key Features of Grafana

| Feature | Description |
|---|---|
| Dashboards | Real-time monitoring dashboards |
| Multi Data Source Support | Supports Prometheus, Loki, Elasticsearch, etc. |
| Alerting | Configure alert notifications |
| Plugins | Extend Grafana functionality |
| Templating | Dynamic dashboards using variables |
| Security | RBAC, LDAP, OAuth, HTTPS support |

---

## 🔹 Important Grafana Definitions

| Term | Definition |
|---|---|
| Dashboard | Collection of panels organized into a grid |
| Panel | Visualization of metrics such as graphs, tables, gauges |
| Data Source | Backend system providing data to Grafana |
| Alert Rule | Condition used to trigger notifications |
| Variable | Dynamic value used in dashboard queries |
| Query | Command used to fetch metrics |
| Loki | Grafana log aggregation system |
| Annotation | Marker showing events on graphs |
| Organization | Logical grouping of users and dashboards |
| Folder | Used to organize dashboards |

---

# 🛠️ 2. Key Concepts

## 🔹 Dashboard

A dashboard is a collection of visualization panels used to monitor systems and applications.

---

## 🔹 Panel

Panels display visualized data such as:

- Graphs
- Gauges
- Tables
- Pie Charts
- Heatmaps

---

## 🔹 Data Sources

Grafana supports multiple data sources including:

- Prometheus
- Loki
- Elasticsearch
- InfluxDB
- MySQL

---

## 🔹 Alerting

Grafana alerting allows users to configure notifications when metrics cross thresholds.

---

# 🐳 3. Grafana Installation

## 🐧 Install Grafana on Ubuntu/Debian

### Install Required Packages

```bash
sudo apt-get install -y adduser libfontconfig1
```

---

### Download Grafana

```bash
wget https://dl.grafana.com/oss/release/grafana_7.5.7_amd64.deb
```

---

### Install Grafana

```bash
sudo dpkg -i grafana_7.5.7_amd64.deb
```

---

### Start Grafana Service

```bash
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

---

## 🐳 Install Grafana Using Docker

```bash
docker run -d \
-p 3000:3000 \
--name=grafana \
grafana/grafana
```

---

## 🌐 Access Grafana

Open browser:

```text
http://localhost:3000
```

Default credentials:

```text
Username: admin
Password: admin
```

---

# 🔌 4. Configuring Data Sources

## 🔹 Add Prometheus Data Source

Steps:

1. Navigate to Configuration → Data Sources
2. Click Add data source
3. Select Prometheus
4. Enter Prometheus URL

Example:

```text
http://localhost:9090
```

5. Click Save & Test

---

## 🔹 Add Elasticsearch Data Source

Steps:

1. Navigate to Configuration → Data Sources
2. Select Elasticsearch
3. Enter:

- URL
- Index name
- Time field

4. Click Save & Test

---

# 📈 5. Building Dashboards

## 🔹 Create a Dashboard

Steps:

1. Click "+" icon in sidebar
2. Select Dashboard
3. Click Add new panel
4. Choose data source
5. Write query
6. Select visualization type
7. Save dashboard

---

## 🔹 Example PromQL Query

```promql
rate(http_requests_total[5m])
```

---

## 🔹 Visualization Types

| Visualization | Purpose |
|---|---|
| Graph | Time-series visualization |
| Gauge | Threshold monitoring |
| Stat | Single metric display |
| Table | Structured data display |
| Heatmap | Density visualization |

---

## 🔹 Using Variables

### Create Variable

1. Go to Dashboard Settings → Variables
2. Click New
3. Configure:

- Name
- Type
- Query

---

### Example Variable Usage

```text
$instance
$job
$namespace
```

---

# 🚨 6. Grafana Alerting

## 🔹 Creating Alerts

Steps:

1. Add a panel
2. Open Alert tab
3. Click Create Alert
4. Set alert conditions
5. Configure evaluation interval
6. Configure notification channel

---

## 🔹 Notification Channels

Supported channels:

- Email
- Slack
- Microsoft Teams
- Discord
- PagerDuty
- Webhooks

---

## 🔹 Example Alert Condition

```text
WHEN avg() OF query(A, 5m, now) IS ABOVE 80
```

---

# 🔌 7. Grafana Plugins

## 🔹 Install Plugins

```bash
grafana-cli plugins install grafana-piechart-panel
```

---

## 🔹 Restart Grafana

```bash
sudo systemctl restart grafana-server
```

---

## 🔹 Popular Plugins

| Plugin | Purpose |
|---|---|
| Pie Chart Panel | Display metrics in pie chart |
| Worldmap Panel | Geographic visualization |
| Alert List Panel | Show active alerts |
| Clock Panel | Timezone clocks |
| Kubernetes App | Kubernetes monitoring |

---

# 📊 8. Dashboard Templating

## 🔹 Templated Dashboards

Templating allows dashboards to become dynamic based on selected variables.

---

## 🔹 Dynamic Panels

Grafana supports repeating:

- Panels
- Rows
- Dashboards

Based on variable values.

---

## 🔹 Example Variable Query

```promql
label_values(up, instance)
```

---

# 🎨 9. Customizing Grafana

## 🔹 Themes

Grafana supports:

- Dark Theme
- Light Theme

---

## 🔹 Custom Branding

You can customize:

- Logos
- Colors
- Login screen
- Dashboard appearance

---

## 🔹 Dashboard Preferences

Customize:

- Timezone
- Refresh interval
- Home dashboard

---

# 🔒 10. Securing Grafana

## 🔹 User Management

Grafana roles:

| Role | Access |
|---|---|
| Viewer | Read-only access |
| Editor | Modify dashboards |
| Admin | Full administrative access |

---

## 🔹 LDAP / SSO Integration

Grafana supports:

- LDAP
- OAuth
- Google Login
- GitHub Login
- Azure AD

---

## 🔹 Enable HTTPS

```ini
[server]
protocol = https
cert_file = /path/to/cert.crt
cert_key = /path/to/cert.key
```

---

## 🔹 Authentication Methods

Supported authentication:

- Basic Authentication
- LDAP
- OAuth2
- SAML

---

# 🚀 11. Advanced Queries & Visualizations

## 🔹 Grafana with PromQL

Use advanced PromQL queries for complex monitoring.

Example:

```promql
sum(rate(container_cpu_usage_seconds_total[5m])) by (pod)
```

---

## 🔹 Annotations

Annotations help mark:

- Deployments
- Failures
- Incidents
- Maintenance windows

On dashboards.

---

## 🔹 Mixed Data Sources

Grafana supports combining:

- Metrics
- Logs
- Traces

Within a single dashboard.

---

# 📜 12. Grafana Loki

## 🔹 What is Loki?

Grafana Loki is a horizontally scalable log aggregation system inspired by Prometheus.

Used for:

- Centralized logging
- Log querying
- Log visualization

---

## 🔹 Run Loki Using Docker

```bash
docker run -d \
--name=loki \
-p 3100:3100 \
grafana/loki:2.2.0 \
-config.file=/etc/loki/local-config.yaml
```

---

## 🔹 Query Logs in Grafana

Use Loki as a data source to visualize logs alongside metrics.

---

# ☸️ 13. Grafana in Kubernetes

## 🔹 Deploy Grafana in Kubernetes

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: grafana

spec:
  replicas: 1

  selector:
    matchLabels:
      app: grafana

  template:

    metadata:
      labels:
        app: grafana

    spec:

      containers:

      - name: grafana
        image: grafana/grafana:7.5.7

        ports:
        - containerPort: 3000
```

---

## 🔹 Grafana with Prometheus Operator

Common deployment methods:

- Helm Charts
- kube-prometheus-stack

---

## 🔹 Kubernetes Monitoring

Grafana monitors:

- Nodes
- Pods
- Containers
- Namespaces
- Cluster health

---

# 🛠️ 14. Troubleshooting Grafana

## 🔹 No Data in Dashboard

Check:

- Data source connection
- Query syntax
- Time range
- Network access

---

## 🔹 Slow Dashboards

Optimize:

- Queries
- Refresh intervals
- Time ranges

---

## 🔹 Plugin Errors

Verify:

- Plugin compatibility
- Grafana version
- Correct installation

---

## 🔹 View Grafana Logs

```bash
sudo tail -f /var/log/grafana/grafana.log
```

---

## 🔹 Test Prometheus Connectivity

```bash
curl http://localhost:9090
```

---

# 📚 15. References

## 🔹 Official Documentation

- Grafana Official Documentation

---

## 🔹 Community Resources

- Grafana Labs
- Grafana GitHub Repository
- Loki Documentation
- Grafana Plugin Marketplace

---

# 🎯 Final Takeaway

Grafana is one of the most powerful monitoring and observability platforms used in DevOps and Cloud environments.

It helps teams:

- Visualize infrastructure metrics
- Analyze logs
- Configure alerts
- Monitor Kubernetes
- Improve observability

---

<p align="center">

📊 Grafana Makes Monitoring & Observability Powerful 🚀

</p>
