# Bit-Reborn PDF Project Infrastructure

Infrastructure as Code for deploying the Bit-Reborn PDF backend API on AWS. This repo contains Terraform modules, Kubernetes configs, CI/CD pipelines, and everything needed to deploy and manage the application.

## What This Does

Deploys a backend API with three different profiles depending on your needs:

- **minimal**: Single EC2 instance running Docker Compose (~$15-30/month). Good for dev and learning.
- **standard**: ECS Fargate with load balancer (~$50-80/month). Good for staging and small production.
- **production**: Full EKS cluster with high availability (~$150-300/month). For real production workloads.

All three use the same codebase - you just change a Terraform variable to switch between them.

## Repository Structure

```
terraform/          - Terraform modules and environment configs
kubernetes/         - K8s manifests and Helm charts (for production profile)
docker/             - Dockerfiles and docker-compose.yml
ansible/            - Ansible playbooks for server config
scripts/            - Helper scripts for deployment and operations
.github/workflows/  - GitHub Actions CI/CD pipelines
monitoring/         - Prometheus, Grafana, and alert configs
docs/               - Documentation
```

## Quick Start

You'll need:
- AWS CLI configured
- Terraform installed
- Docker installed
- kubectl (only for production profile)

To deploy the minimal profile:

```bash
cd terraform/envs/dev
terraform init
terraform plan
terraform apply
```

Check the docs/getting-started.md for detailed setup instructions.

## Documentation

**For beginners:**
- docs/getting-started.md - How to set up your environment
- docs/learning-path.md - Step-by-step guide through all phases
- aminu_init_guide.md - Explains what every folder does

**Reference docs:**
- docs/architecture.md - System design and decisions
- docs/deployment-guide.md - How to deploy each profile
- docs/cost-comparison.md - Cost breakdown

**Operations:**
- docs/runbooks/deploy.md - Deployment procedures
- docs/runbooks/rollback.md - How to rollback
- docs/runbooks/troubleshooting.md - Common problems

## Tech Stack

- Terraform for infrastructure
- Docker for containerization
- ECS or EKS for orchestration (depending on profile)
- GitHub Actions for CI/CD
- Ansible for configuration management
- Prometheus + Grafana for monitoring
- CloudWatch for logs

## CI/CD Flow

1. Push code or open PR → CI runs (lint, test, build)
2. Merge to main → Auto-deploys to dev
3. Manual deploy → Staging (requires approval)
4. Manual deploy → Production (requires approval)

## Current Status

- Repository structure: Done
- Documentation: Done
- Phase 1 (Containerization): Not started
- Phase 2 (Terraform): Not started
- Phase 3 (CI/CD): Not started
- Phase 4 (ECS): Not started
- Phase 5 (EKS): Not started
- Phase 6 (Monitoring): Not started

## Learning Focus

This project is built for learning. Each component has documentation explaining why it exists and how it works. The goal is to understand everything, not just copy-paste commands.

You'll learn Terraform, Docker, Kubernetes, CI/CD, monitoring, and AWS architecture by actually building this.

## License

[Add your license here]

## Author

Aminu Iliyasu
