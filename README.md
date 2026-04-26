# 📊 Kubernetes Monitoring & Observability Stack

Production-grade monitoring and observability stack deployed on Kubernetes using Prometheus, Grafana, and ELK Stack.

## 🏗️ Stack Overview

| Tool | Purpose | Port |
|------|---------|------|
| Prometheus | Metrics collection and alerting | 9090 |
| Grafana | Metrics visualization and dashboards | 3000 |
| Elasticsearch | Log storage and search | 9200 |
| Logstash | Log processing and parsing | 5044 |
| Kibana | Log visualization | 5601 |

## 🔄 Architecture

| Layer | Flow |
|-------|------|
| **Metrics** | App Pods → Prometheus Scrape → Grafana Dashboard |
| **Logs** | App Pods → Logstash → Elasticsearch → Kibana |
| **Alerts** | Prometheus Rules → Alertmanager → Slack/Email |

## 📁 Project Structure

| Path | Purpose |
|------|---------|
| `prometheus/prometheus-config.yaml` | Scrape configs and alert rules |
| `prometheus/deployment.yaml` | Prometheus deployment |
| `grafana/deployment.yaml` | Grafana deployment |
| `grafana/datasource-config.yaml` | Prometheus and ES datasources |
| `elk/elasticsearch.yaml` | Elasticsearch deployment and service |
| `elk/logstash-config.yaml` | Log parsing pipeline |
| `elk/kibana.yaml` | Kibana deployment and service |
| `alerting/alert-rules.yaml` | Kubernetes alert rules |

## 🚨 Alert Rules Configured

| Alert | Condition | Severity |
|-------|-----------|---------|
| PodCrashLooping | Pod restarting > 0 times in 5m | Critical |
| NodeHighCPU | CPU usage > 85% | Warning |
| NodeHighMemory | Memory usage > 85% | Warning |
| PodNotReady | Pod not ready for 5m | Critical |
| DeploymentReplicasMismatch | Available replicas != desired | Warning |

## 🚀 Deployment

```bash
# Create monitoring namespace
kubectl create namespace monitoring

# Deploy Prometheus
kubectl apply -f prometheus/

# Deploy Grafana
kubectl apply -f grafana/

# Deploy ELK Stack
kubectl apply -f elk/

# Apply Alert Rules
kubectl apply -f alerting/
```

## 📊 Key Achievements

- ✅ Improved MTTR by **30%** through centralized monitoring
- ✅ Real-time alerting for **5 critical** Kubernetes conditions
- ✅ Centralized log management across all namespaces
- ✅ Custom Grafana dashboards for CPU, Memory, Pod health

## 👤 Author
**Lokesh Kumar Reddy** — [LinkedIn](https://www.linkedin.com/in/lokesh-kumar-reddy-mandireddy-a1b0a122a) | [GitHub](https://github.com/LokeshReddie456)