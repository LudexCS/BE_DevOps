# Ludex DevOps - CI/CD Repository

This repository manages the CI/CD pipelines and deployment manifests for the Ludex platform's microservices.

## 🔧 Responsibilities

- Builds and deploys Docker images via GitHub Actions
- Applies Kubernetes manifests to the internal k3s cluster
- Handles service-wise deployments on push to `main` branches
- Secures sensitive variables via GitHub Secrets

## 📦 Managed Microservices

- `BE_UserAccount`
- `BE_Web3Gateway`
- `BE_Upload`
- `BE_Management`

## 🛠 Folder Structure

- `.github/workflows`: GitHub Actions pipelines
- `manifests/`: Kubernetes deployment files (organized by service)
- `scripts/`: Deployment or notification utilities (optional)

## 🔐 Security

All secrets such as SSH keys, database credentials, and Docker tokens are managed through GitHub Secrets and are **never committed** to this repository.

## 📣 How it works

Each microservice repo triggers this repo via `repository_dispatch` on merge to `main`, which pulls the latest manifest and applies it to the k3s cluster running on EC2.