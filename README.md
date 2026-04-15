# Cloud-Native Observability Platform on EKS

## 🚀 Overview

This project demonstrates a **production-grade observability platform** built on Kubernetes using the Grafana stack with OpenTelemetry.

The system is designed to handle **high-scale telemetry ingestion (20K+ distributed .NET agents)** and provides centralized monitoring for:

* Metrics
* Logs
* Traces

---

## 🧱 Stack

* Grafana (Visualization & Alerting)
* Prometheus (Metrics)
* Loki (Logs → S3)
* Tempo (Traces → S3)
* OpenTelemetry Collector (Gateway + Internal)
* Kubernetes (EKS-ready)

---

## 🧠 Architecture

```
.NET Agents
    ↓
OpenTelemetry Collector
    ↓
-------------------------
| Prometheus (metrics) |
| Loki (logs)         |
| Tempo (traces)      |
-------------------------
    ↓
Grafana
```

---

## 📊 Features

* Scalable architecture supporting **20K+ agents**
* Secure telemetry ingestion (TLS + authentication)
* Separation of ingestion and processing layers
* S3-based storage for logs and traces
* Preconfigured dashboards and alerting
* Optimized pipelines for metrics, logs, and traces

---

## ☁️ AWS Infrastructure

* Amazon EKS (Kubernetes)
* Amazon S3 (Loki & Tempo storage)
* EBS volumes (Prometheus)
* AWS Load Balancer (Ingress)
* TLS via cert-manager / ACM

---

## 🔄 Data Flow

1. .NET agents send telemetry using OpenTelemetry (OTLP)
2. Public OTEL Collector receives data securely
3. Data is forwarded to internal collectors
4. Metrics → Prometheus
5. Logs → Loki → S3
6. Traces → Tempo → S3
7. Grafana visualizes all signals

---

## 📂 Project Structure

```
helm/        → Helm values for all components
k8s/         → Kubernetes manifests
otel/        → OTEL collector configurations
dashboards/  → Grafana dashboards
alerts/      → Prometheus alert rules
docs/        → Documentation & best practices
```

---

## 📈 Scaling Strategy

* Horizontal scaling of OTEL collectors
* Prometheus retention tuning
* Loki using boltdb-shipper + S3
* Tempo distributed architecture
* Load-balanced ingestion layer

---

## 🔐 Security

* TLS for all external endpoints
* Authentication for OTEL ingestion
* Namespace isolation
* Optional mTLS support

---

## 🧪 Load Simulation

Telemetry load can be simulated using OpenTelemetry load generators and k6 to mimic thousands of distributed agents.

---

## ⚙️ Deployment

Step-by-step guide available in:

docs/deployment.md

---

## 📸 Screenshots

(Add Grafana dashboards here)

---

## 📚 Best Practices

* Use OTEL gateway for external ingestion
* Avoid direct ingestion into backends
* Use object storage for scalability
* Monitor collector performance
* Apply rate limiting on public endpoints

---

## 👨‍💻 Author

DevOps Engineer focused on Kubernetes, Observability, and Cloud-Native systems.

What you just built (this is BIG)
📊 Metrics

Prometheus
→ collects cluster + app metrics

📜 Logs

Loki
→ stores and queries logs

🔍 Traces

Tempo
→ distributed tracing backend

🔗 Collector (ingestion brain)

OpenTelemetry Collector
→ routes all telemetry data

📊 UI

Grafana
→ dashboards + visualization

