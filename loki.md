
# Loki Monitoring Overview

## What is Loki?
Loki is a log aggregation system designed by Grafana Labs, inspired by Prometheus. Unlike other logging systems, Loki indexes only metadata (labels), not the full log content.

---

## Key Features of Loki
- **Scalable and Cost-effective:** Only indexes labels, not full text.
- **Grafana Integration:** Seamlessly integrates with Grafana for querying and visualization.
- **Multi-tenancy Support**
- **Promtail Agent:** Gathers logs and ships to Loki.

---

## Components of Loki
1. **Loki Server:** Receives, stores, and queries logs.
2. **Promtail:** Log shipping agent (like Fluentd or Logstash).
3. **Grafana:** UI for querying and visualizing logs from Loki.

---

## Installing Loki with Docker
```bash
docker run -d --name=loki -p 3100:3100 grafana/loki
```

---

## Installing Promtail
Promtail tails logs and ships them to Loki.
```bash
docker run -d -v /var/log:/var/log -v /etc/promtail:/etc/promtail grafana/promtail
```

---

## Loki Configuration
- Loki config: `loki-config.yaml`
- Promtail config: `promtail-config.yaml`

---

## Querying Logs in Grafana
Loki uses **LogQL** (Log Query Language).
```logql
{job="nginx"} |= "GET"
```

### LogQL Filters:
- `|=`: exact match
- `!=`: exclude
- `|~`: regex match
- `!~`: regex exclude

---

## Example Use Case
You want to see error logs from a microservice:
```logql
{job="my-service"} |= "error"
```

---

## Alerts with Logs
Using Loki with Alertmanager and Grafana to trigger alerts based on log queries.

---

## Summary
- Loki is a powerful, lightweight logging solution.
- It works best with Grafana and Promtail.
- LogQL provides powerful querying for log data.
