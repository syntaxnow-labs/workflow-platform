# workflow-platform
A central repository containing reusable GitHub Actions workflows for all your apps (Node, Java, React, Spring Boot, whatever your future self builds).

This repository acts as a central CI/CD engine for all services.
Instead of duplicating YAML files in every repo, applications can simply call these workflows using:

```yaml
uses: YOUR-ORG/workflow-platform/.github/workflows/quality-check-node.yml@main
```

## 🔧 Included Workflows

| Workflow                 | Purpose                                                                      |
|--------------------------| ---------------------------------------------------------------------------- |
| `quality-check-node.yml` | Runs quality checks for any Node/React/NextJS project (lint, tests, etc.)    |
| `quality-check-java.yml` | Runs quality checks for any Java/Spring Boot service (compile, tests, etc.)  |
| `deploy-gitops.yml`      | Build Docker → Push to GHCR → Update GitOps repo → Trigger ArgoCD deployment |

## 📁 Repository Structure
```sh
.github/workflows/   → reusable workflow YAMLs
scripts/             → helper scripts used during builds
```

## 🚀 Usage
In any application repo:
```yaml
jobs:
  build:
    uses: YOUR-ORG/workflow-platform/.github/workflows/quality-check-node.yml@main
```

## 🧬 GitOps Ready

This repo is designed for:
 - GHCR container registry
 - GitOps repo auto-updates
 - ArgoCD auto-sync
 - Kubernetes deployments (k3s, k8s, AKS, etc.)
