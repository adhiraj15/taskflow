# TaskFlow — Cloud & DevOps Project

TaskFlow is a simple Python Flask application created to practise a fresher-level DevOps workflow.

## Tools Used

- Linux
- Git and GitHub
- AWS EC2 (practice environment)
- Docker
- Jenkins and CI/CD
- Kubernetes with Minikube
- Helm
- Prometheus and Grafana

## What I Practised

- Managed application code using Git and GitHub.
- Created a Docker image using a Dockerfile.
- Configured a Jenkins pipeline and tested a GitHub webhook.
- Deployed and managed the application using Kubernetes.
- Practised ConfigMaps, Secrets, health checks, persistent storage and autoscaling.
- Monitored Kubernetes CPU, memory and namespace resource usage using Prometheus and Grafana.

## Project Workflow

1. Maintain application source code in GitHub.
2. Build a Docker image for the application.
3. Use Jenkins to automate GitHub checkout, Docker build/run, and the application health check.
4. Practise Kubernetes deployment separately using the manifests in the `kubernetes/` directory.
5. Configure application settings, storage and scaling.
6. Monitor Kubernetes resources through Grafana dashboards.

## Repository Structure

- `app/` — Python Flask application and dependencies
- `Dockerfile` — instructions for building the Docker image
- `Jenkinsfile` — Jenkins pipeline configuration
- `kubernetes/` — Deployment, Service, ConfigMap, Secret example, PVC and HPA manifests
- `monitoring/` — Prometheus and Grafana configuration and documentation
- `docs/screenshots/` — selected project screenshots

## Kubernetes Features Practised

- Pods, Deployments and Services
- Scaling, rolling updates and rollback
- ConfigMaps and Kubernetes Secrets
- PersistentVolumeClaims
- Resource requests, limits and HPA

## Monitoring

Prometheus collects metrics, while Grafana displays monitoring dashboards.

The Kubernetes / Compute Resources / Cluster dashboard was used to view CPU utilisation, memory utilisation, resource requests and limits, and namespace-wise CPU usage.

See [Monitoring Documentation](monitoring/README.md) and the configuration in `monitoring/values.yaml`.

## Screenshots

Browse all Jenkins and Grafana screenshots in the [Project Screenshot Gallery](docs/screenshots/README.md).

## Notes and Security

- The application runs on port `5000`.
- The Kubernetes practice environment uses Minikube.
- Never commit real passwords, tokens, private keys or Kubernetes Secret values.
- Use SSH tunnelling for private dashboards.
- Review repository contents before making the repository public.

## Learning Goal

Gain practical experience with core DevOps tools and be able to explain how the application is built, deployed, monitored and troubleshot.
