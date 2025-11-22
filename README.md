📦 Voting App – DevOps Multi-Phase Project

This repository contains a multi-phase DevOps project built around a simple microservices-based Voting Application.
The goal is to demonstrate practical DevOps skills across containerization, orchestration, automation, and CI/CD.

🚀 Project Overview

The application consists of five microservices:

vote – Public-facing frontend for casting votes

result – Displays the aggregated voting results

worker – Background processor syncing votes from Redis to PostgreSQL

redis – In-memory datastore

db (PostgreSQL) – Persistent datastore

🧩 Phase 1 – Containerization & Local Development

Dockerfiles for all services

docker-compose.yml for running the full app locally

☸️ Phase 2 – Kubernetes Deployment (with Helm)

This phase includes a full Helm chart and supporting Kubernetes manifests.

Features:

Deployments, Services, ConfigMaps, Secrets

Ingress configuration

Horizontal Pod Autoscaling (optional)

Resource requests/limits

Liveness & readiness probes

Production-ready Redis & Postgres deployments using StatefulSets + PVCs

Separate values files for dev and prod environments

Structure Example:
helm/
  voting-app/
    templates/
    values.yaml
    values-prod.yaml
k8s-manifests/


🔄 Phase 3 – CI/CD Pipeline (GitHub Actions)

The project includes a CI/CD workflow that:

Builds and tags Docker images

Pushes images to a container registry

Runs linting on Kubernetes/Helm files

Deploys the application to a Kubernetes cluster using Helm

About the Deployment

CI/CD successfully builds and pushes all images.
Deployment to Kubernetes works, but I ran into namespace-related issues during automated deployment.
Instead of overengineering with temporary fixes, I kept the pipeline simple and transparent.

This still demonstrates:

End-to-end automation

Helm-based deployment flow

Real troubleshooting scenarios

Practical DevOps thinking and debugging

(If needed, I can provide notes on the exact namespace issue.)

🗄 Database & Redis – Production Deployment
PostgreSQL:

StatefulSet

PersistentVolumeClaim

Secrets for credentials

Configurable storage

Redis:

StatefulSet

Persistence enabled

Probes, limits, and optional password

📁 Repository Structure 
/vote
/result
/worker
/docker-compose.yml
/helm
/k8s-manifests
/.github/workflows
README.md

▶️ Local Development
docker-compose up --build

☸️ Deploying to Kubernetes
Dev:
helm install voting-app ./helm/voting-app -f values.yaml

Prod:
helm install voting-app ./helm/voting-app -f values-prod.yaml


🔍 Notes


This project focuses on showing real DevOps workflows—not just perfect demos.


The CI/CD pipeline reflects a real environment where issues (e.g., namespaces) appear and require troubleshooting.


Infrastructure follows a clean, modular structure suitable for scaling.

Container networking & environment variables

Easy setup for testing and local DevOps workflows
