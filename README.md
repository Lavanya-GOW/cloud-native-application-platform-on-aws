# ☁️ AWS Three-Tier Architecture

### Production-Inspired Infrastructure on AWS using Terraform, Docker, Kubernetes (k3s), GitHub Actions, Prometheus & Grafana.

[![Terraform](https://img.shields.io/badge/Terraform-844FBA?logo=terraform&logoColor=white)](https://www.terraform.io/)
[![AWS](https://img.shields.io/badge/AWS-FF9900?logo=amazonaws&logoColor=white)](https://aws.amazon.com/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?logo=githubactions&logoColor=white)](https://github.com/features/actions)
[![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?logo=prometheus&logoColor=white)](https://prometheus.io/)
[![Grafana](https://img.shields.io/badge/Grafana-F46800?logo=grafana&logoColor=white)](https://grafana.com/)
[![Argo CD](https://img.shields.io/badge/Argo_CD-EF7B4D?logo=argo&logoColor=white)](https://argo-cd.readthedocs.io/)
[![Loki](https://img.shields.io/badge/Loki-F2F4F7?logo=grafana&logoColor=black)](https://grafana.com/oss/loki/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Production-inspired AWS Infrastructure demonstrating Infrastructure as Code, CI/CD, Docker image automation, Kubernetes deployments and scalable cloud architecture.

---

# 📖 Overview

This project is a production-inspired **three-tier cloud-native application platform** built to understand and implement modern infrastructure engineering practices end-to-end.

The project has evolved from a Terraform-based AWS architecture into a broader platform combining:

- Infrastructure as Code with **Terraform**
- Containerization with **Docker**
- Kubernetes orchestration using **k3s**
- Automated CI/CD with **GitHub Actions**
- GitOps-based deployment with **Argo CD**
- Metrics and monitoring with **Prometheus & Grafana**
- Alerting with **Alertmanager**
- Centralized logging with **Loki & Grafana Alloy**
- AWS networking and infrastructure
- Application health checks, service discovery and automated reconciliation

The focus is not simply on deploying an application, but on understanding how infrastructure, application delivery, observability and automation work together as a real platform.

---

# 🎯 Why I Built This

The primary objective of this project was to move beyond learning individual AWS services and instead understand how production systems are actually engineered.

This repository focuses on:

- Reproducible infrastructure
- Automated application delivery
- Kubernetes-based orchestration
- Infrastructure and application observability
- GitOps and declarative operations
- Failure detection and recovery
- Security and reliability
- Automation with minimal manual intervention
- Production-oriented engineering practices

The goal was understanding **why production infrastructure is designed the way it is.**

---

# 🏗 Architecture

```text
                         ┌──────────────────────┐
                         │      Developer       │
                         │   Code / Git Push    │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │    GitHub Actions    │
                         │ Build • Test • Docker │
                         │   Push • Update Git  │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │       GitHub         │
                         │ Kubernetes Desired   │
                         │       State          │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │       Argo CD        │
                         │ GitOps Reconciliation│
                         │ Self-Heal • Pruning  │
                         └──────────┬───────────┘
                                    │
                                    ▼
Internet ──► AWS Load Balancer ──► Kubernetes Ingress
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │      k3s Cluster     │
                         │                      │
                         │ ┌──────────────────┐ │
                         │ │    Frontend      │ │
                         │ └────────┬─────────┘ │
                         │          │            │
                         │ ┌────────▼─────────┐ │
                         │ │     Backend      │ │
                         │ └────────┬─────────┘ │
                         │          │            │
                         │ ┌────────▼─────────┐ │
                         │ │      Redis       │ │
                         │ └──────────────────┘ │
                         └──────────┬───────────┘
                                    │
                                    ▼
                              AWS RDS Database


        ┌─────────────────────────────────────────────┐
        │             Observability Layer             │
        │                                             │
        │ Prometheus → Metrics                        │
        │ Grafana    → Dashboards                     │
        │ Alertmanager → Alerts                       │
        │ Alloy      → Log Collection                 │
        │ Loki       → Centralized Log Storage        │
        └─────────────────────────────────────────────┘
```

# ☁ Infrastructure Components

| Service             | Purpose                 |
| ------------------- | ----------------------- |
| VPC                 | Network Isolation       |
| Public Subnets      | Load Balancer & Bastion |
| Application Subnets | Worker Nodes            |
| Database Subnets    | PostgreSQL              |
| Internet Gateway    | Public Connectivity     |
| NAT Gateway         | Private Internet Access |
| Security Groups     | Network Security        |
| Bastion Host        | Secure SSH              |
| External ALB        | Public Entry            |
| Control Plane       | Kubernetes API          |
| Worker ASG           | Kubernetes Workers      |
| IAM                 | Secure AWS Permissions  |
| SSM Parameter Store | Cluster Join Token      |
| RDS PostgreSQL      | Database                |
| Redis               | Cache                   |
| Kubernetes          | Orchestration           |
| Ingress             | Traffic Routing         |
| ConfigMaps          | Runtime Config          |
| Prometheus          | Metrics Collection & Monitoring |
| Grafana             | Metrics Visualization & Dashboards |
| ServiceMonitor      | Kubernetes Service Metrics Discovery |
| Argo CD             | GitOps deployment and reconciliation |
| Alertmanager        | Alert routing           |
| Loki                | Centralized log storage |
| Grafana Alloy       | Log collection and forwarding |
---

# 🚀 Features

### Infrastructure

- AWS infrastructure provisioned using Terraform
- Reproducible networking and compute configuration
- Public/private architecture
- Security groups and controlled network access
- RDS integration
- Infrastructure lifecycle through Terraform

### Containers

- Separate frontend and backend Docker images
- Reproducible application environments
- Docker image smoke testing in CI
- Versioned container images using Git commit SHA

### Kubernetes

- k3s-based Kubernetes cluster
- Frontend and backend Deployments
- Redis StatefulSet
- Kubernetes Services
- ConfigMaps
- Namespaces
- Ingress
- Health probes
- Service discovery
- Replica management

### CI/CD

- GitHub Actions triggered by application changes
- Dependency installation and validation
- Application smoke tests
- Docker image builds
- Docker Hub publishing
- Automatic Kubernetes manifest updates
- Git-based deployment workflow

### GitOps

- Argo CD continuously watches Git
- Git acts as the declarative source of truth
- Automated synchronization
- Drift detection
- Self-healing
- Pruning of resources removed from desired state

### Observability

- Prometheus metrics
- Grafana dashboards
- Alertmanager alerts
- Loki centralized logs
- Alloy log collection
- Kubernetes workload monitoring

---

# 📊 Monitoring & Observability

## Prometheus

Prometheus collects Kubernetes and application metrics.

The monitoring stack includes:

- Prometheus
- kube-state-metrics
- node-exporter
- ServiceMonitors
- Alertmanager
- Grafana

Example metrics include:

- CPU usage
- Memory usage
- Pod state
- Deployment state
- Node health
- Container resource usage
- Application metrics

## 📈 Grafana

Grafana provides dashboards for infrastructure and application metrics.

```text
Kubernetes / Application
          │
          ▼
      Prometheus
          │
          ▼
        Grafana
```

---

# 🚨 Alertmanager

Alertmanager handles alerts generated by Prometheus.

It provides:

- Alert routing
- Grouping
- Deduplication
- Notification handling

This moves the monitoring system beyond passive dashboards toward active failure detection.

---

# 📝 Centralized Logging

The project uses **Grafana Alloy + Loki** for centralized logging.

```text
Application Pods
      │
      ▼
   Grafana Alloy
      │
      ▼
      Loki
      │
      ▼
    Grafana
```

### Alloy

Alloy collects and forwards logs from the Kubernetes environment.

### Loki

Loki stores logs centrally and makes them queryable through Grafana.

This enables troubleshooting without manually inspecting every container or node.

---

# 🔐 Security Model

Security is treated as an engineering requirement rather than a separate add-on.

Current practices include:

- AWS Security Groups
- Public/private network separation
- IAM-based AWS access
- SSM-based instance management
- Kubernetes namespaces
- Controlled service exposure
- GitHub repository permissions
- Limited GitHub Actions token permissions
- Traceable Docker image versions

Future hardening areas include:

- Kubernetes NetworkPolicies
- Container image vulnerability scanning
- Secrets management
- Least-privilege IAM
- Pod security hardening
- Runtime security
- Software supply-chain security

---

# ⚙️ Reliability, Availability & Scalability

The next phase focuses on production hardening.

### Reliability

- Health probes
- Automated reconciliation
- Self-healing
- Failure detection
- Controlled rollouts
- Rollback strategies

### Availability

- Multiple application replicas
- Kubernetes scheduling
- Load balancing
- Failure recovery
- Database availability considerations

### Scalability

Planned improvements include:

- Horizontal Pod Autoscaler
- Metrics Server
- Cluster Autoscaler
- Resource requests and limits
- Load testing
- Performance benchmarking

---

# 🧪 Validation & Engineering Experiments

The project is validated through practical experiments rather than configuration alone.

### GitOps Drift Detection

A Kubernetes Deployment was manually changed:

```bash
kubectl scale deployment backend -n three-tier-app --replicas=2
```

Argo CD detected the difference between live state and Git state.

### Self-Healing

Argo CD automatically restored the Deployment to the desired replica count.

### CI/CD

A backend code change successfully triggered:

```text
Code change
   ↓
GitHub Actions
   ↓
Application validation
   ↓
Docker build
   ↓
Docker smoke test
   ↓
Docker Hub push
   ↓
Manifest update
   ↓
Git commit
   ↓
Argo CD sync
   ↓
Kubernetes rollout
```

This validates the complete application delivery chain.

---

# 🧠 Engineering Principles

### 1. Declarative Infrastructure

Infrastructure should describe the desired state rather than require manual step-by-step configuration.

### 2. Git as Source of Truth

Infrastructure and deployment configuration should be version-controlled.

### 3. Automation First

Repeated manual operations should become automated workflows.

### 4. Immutable Artifacts

Container images should be traceable to specific source revisions.

### 5. Reconciliation

Systems should continuously move actual state toward desired state.

### 6. Observability

A system is not production-ready if its health cannot be measured and its failures cannot be investigated.

### 7. Minimal Manual Intervention

The goal is to allow developers and operators to interact with the platform through simple, repeatable workflows.

---

# 🛠️ Technology Stack

| Category | Technology |
|---|---|
| Cloud | AWS |
| IaC | Terraform |
| Containers | Docker |
| Orchestration | Kubernetes / k3s |
| CI/CD | GitHub Actions |
| GitOps | Argo CD |
| Backend | Python / Flask |
| Frontend | Web Application |
| Cache | Redis |
| Database | Amazon RDS |
| Monitoring | Prometheus |
| Visualization | Grafana |
| Alerting | Alertmanager |
| Logging | Loki |
| Log Collection | Grafana Alloy |
| Instance Management | AWS SSM |
| Source Control | Git / GitHub |

---

# 📂 Repository Structure

```text
├── Backend
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
├── Frontend
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
├── LICENSE
├── Loki
│   └── values.yaml
├── README.md
├── README2.md
├── alertmanager
│   ├── alertmanager-config.yaml
│   ├── gmail-alertmanager-config.yaml
│   └── prometheus-rule.yaml
├── alloy
│   └── values.yaml
├── argocd
│   └── manifest.yaml
├── docker-compose.yml
├── docs
│   ├── architecture.md
│   ├── deployment_notes.md
│   ├── design_descision.md
│   ├── lessons_learned.md
│   └── roadmap.md
├── images
│   ├── Alertmanager-alerts.png
│   ├── Application-alerts.png
│   ├── Application_status.png
│   ├── ArgoCD_Application_UI.png
│   ├── ArgoCD_Details_Tree.png
│   ├── ArgoCD_History&Rollback.png
│   ├── Infrastructure_status.png
│   ├── Kube-alerts.png
│   ├── Kubernetes_status.png
│   ├── Loki_live_logs.png
│   ├── Loki_logs_1.png
│   ├── Loki_logs_2.png
│   ├── Prometheus_status.png
│   ├── Videos - Shortcut.lnk
│   └── architecture.png
├── kubernetes-files
│   ├── backend
│   │   ├── backend-deployment.yaml
│   │   └── backend-service.yaml
│   ├── base
│   │   ├── configmaps.yaml
│   │   └── namespace.yaml
│   ├── frontend
│   │   ├── frontend-deployment.yaml
│   │   └── frontend-service.yaml
│   ├── ingress.yaml
│   └── redis
│       ├── redis_service.yaml
│       └── statefulset.yaml
├── monitoring
│   ├── backend-servicemonitor.yaml
│   ├── deployment.yaml
│   ├── frontend-servicemonitor.yaml
│   ├── grafana_dashboard.json.json
│   ├── loki-datasource.yaml
│   ├── namespace.yaml
│   ├── prometheus.yaml
│   └── service.yaml
└── terraform_infra
    ├── alb.tf
    ├── backend.tf
    ├── bastion.tf
    ├── iam.tf
    ├── instance.tf
    ├── output.tf
    ├── rds.tf
    ├── scripts
    │   ├── deploy.sh
    │   ├── server.sh
    │   └── worker.sh
    ├── secrets.tf
    ├── security_groups.tf
    ├── terraform.tf
    ├── terraform.tfstate
    ├── terraform.tfstate.backup
    ├── terraform.tfvars
    ├── variables.tf
    ├── vpc.tf
    └── worker_asg.tf
```

> Some infrastructure and monitoring files may evolve as the platform grows; the structure above represents the main current project organization.

---

# 🗺️ Project Roadmap

## Version 1 — Infrastructure Foundation

- Terraform
- AWS networking
- Security Groups
- Compute
- Load Balancer
- RDS
- Docker
- Initial GitHub Actions automation

## Version 2 — Kubernetes

- Kubernetes/k3s cluster
- Deployments
- Services
- StatefulSets
- ConfigMaps
- Namespaces
- Health probes
- Service discovery

## Version 2.1 — Ingress

- Kubernetes Ingress
- Application routing
- External traffic management

## Version 3 — Self-Managed Kubernetes Platform

- Self-managed k3s cluster
- Control-plane architecture
- Worker nodes
- Application deployments
- SSM-based management
- Frontend/backend separation
- Kubernetes service discovery

## Version 4.0 — Metrics & Monitoring

- Prometheus
- kube-state-metrics
- node-exporter

## Version 4.1 — Visulaization

- Grafana Dashboard
- ServiceMonitors

## Version 4.2 — Alerting

- Alertmanager
- Prometheus alert rules
- Alert routing
- Failure notifications

## Version 4.3 — Centralized Logging

- Grafana Alloy
- Loki
- Centralized Kubernetes logs
- Grafana log visualization

## Version 5 — GitOps

- Argo CD
- Git as deployment source of truth
- Automated synchronization
- Drift detection
- Self-healing
- Resource pruning

---

# 🔮 Future Production Hardening

The next major phase is focused on making the platform more production-grade rather than simply adding more tools.

Planned areas include:

- Kubernetes NetworkPolicies
- Container image scanning
- Secrets management
- Least-privilege IAM
- Resource requests and limits
- Horizontal Pod Autoscaling
- Metrics Server
- Cluster Autoscaling
- Load testing
- Performance optimization
- Distributed tracing
- OpenTelemetry
- Advanced deployment strategies
- Backup and disaster recovery
- High-availability considerations
- Security hardening
- Reliability engineering
- Developer/platform experience improvements

---

# 📌 Current Project Status

The project currently demonstrates an end-to-end cloud-native platform covering:

```text
Infrastructure as Code
        ↓
AWS Infrastructure
        ↓
Docker Containers
        ↓
Kubernetes / k3s
        ↓
CI/CD
        ↓
GitOps / Argo CD
        ↓
Automated Reconciliation
        ↓
Monitoring
        ↓
Alerting
        ↓
Centralized Logging
```

The infrastructure foundation and automated delivery system are now established.

The project is moving into the next stage:

> **Production Hardening — improving security, reliability, availability, scalability, performance and developer experience.**

---

# 🙏 Acknowledgements

This project was built through continuous experimentation with:

- AWS
- Terraform
- Docker
- Kubernetes
- GitHub Actions
- Argo CD
- Prometheus
- Grafana
- Alertmanager
- Loki
- Grafana Alloy

The project is intentionally built as a learning platform for understanding how modern cloud infrastructure and platform engineering systems work together.

---

# ⭐ Thanks for Visiting!

If you found this project useful or interesting, feel free to explore the repository and follow its evolution.

**Built to learn. Built to automate. Built to understand infrastructure.**