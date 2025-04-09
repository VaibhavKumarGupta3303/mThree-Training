# Grafana Learning Summary with Detailed Concepts and Examples

---

## 1. What is Grafana?
Grafana is an open-source observability and data visualization platform. It allows users to query, visualize, and alert on metrics, logs, and traces from various data sources.

🔹 **Use Cases:**
- Monitor application performance
- Track infrastructure health
- Visualize business metrics

---

## 2. Grafana Architecture
- **Frontend (UI):** Web interface for dashboards and settings.
- **Backend:** Handles queries, authentication, and data processing.
- **Database:** Stores user settings, dashboards, and configurations (not actual metrics).

---

## 3. Installing Grafana

### ➤ Docker:
```bash
docker run -d -p 3000:3000 grafana/grafana
```

### ➤ Manual Install:
- Download from https://grafana.com/grafana/download
- Start service:
```bash
sudo systemctl start grafana-server
```

Access Grafana at: `http://localhost:3000`  
Default login: `admin` / `admin`

---

## 4. Grafana Data Sources
Grafana supports a variety of data sources:
- **Prometheus**
- **InfluxDB**
- **MySQL/PostgreSQL**
- **Elasticsearch**
- **Loki (for logs)**

### Steps to Add a Data Source:
1. Go to **Configuration > Data Sources**
2. Click **Add data source**
3. Select a type (e.g., Prometheus)
4. Enter connection details and save

---

## 5. Creating Dashboards & Panels
- **Dashboard:** Collection of visual panels
- **Panel:** Individual visualization (e.g., graph, gauge, table)

### Steps to Create a Dashboard:
1. Click **+ > Dashboard > Add a new panel**
2. Choose a data source
3. Write a query (e.g., PromQL for Prometheus)
4. Select a visualization type
5. Save the dashboard

---

## 6. Visualization Types
- Time Series Graph
- Gauge
- Bar Chart
- Heatmap
- Table
- Logs (with Loki)

Each type supports customization (colors, thresholds, legends, labels).

---

## 7. Templating and Variables
Use variables to make dashboards dynamic.

### Example:
Create a variable `server` with values from a metric label.

Steps:
1. Dashboard > Settings > Variables > New
2. Name: `server`
3. Query: `label_values(up, instance)` (for Prometheus)
4. Use in panel: `$server`

---

## 8. Alerts in Grafana
Grafana supports alerting on metrics.

### Steps:
1. Create/Edit a panel
2. Go to **Alert > Create Alert Rule**
3. Define conditions (e.g., avg CPU > 70%)
4. Set notification channel (Slack, Email, Webhook)

---

## 9. User Authentication & Roles
- Admin
- Editor
- Viewer

### Login Options:
- Basic (username/password)
- OAuth (GitHub, Google, etc.)
- LDAP/SSO

---

## 10. Plugins and Extensions
Grafana supports plugins:
- Data source plugins
- Panel plugins
- App plugins

### Install Plugin:
```bash
grafana-cli plugins install <plugin-id>
```

---

## 11. Grafana with Prometheus
Grafana and Prometheus are commonly used together:
- Prometheus scrapes metrics
- Grafana visualizes them

### Example PromQL Query:
```bash
rate(http_requests_total[1m])
```

---

## 12. Dashboard JSON
Dashboards are stored as JSON. They can be exported, imported, or versioned.

---

## Summary
✔️ Grafana is powerful for monitoring and visualization  
✔️ Supports many data sources and visualization types  
✔️ Includes alerting, templating, plugins, and user roles  
✔️ Works well with Prometheus, Loki, and others
