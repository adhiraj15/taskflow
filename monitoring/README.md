# TaskFlow Monitoring

## Overview

TaskFlow uses Prometheus and Grafana to monitor Kubernetes resources.

- **Prometheus:** Collects and stores metrics.
- **Grafana:** Displays metrics in dashboards.
- **Prometheus Operator:** Manages Prometheus resources.
- **kube-state-metrics:** Exposes Kubernetes object-state metrics.
- **Node Exporter:** Exposes node-level system metrics.

## Tools Used

- Kubernetes with Minikube
- Helm
- Prometheus
- Grafana

## Installation

This monitoring stack is installed using the Prometheus Community Helm chart.

Add or update the Helm repository:

    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts --force-update
    helm repo update

Install or upgrade the monitoring stack from the repository root:

    helm upgrade --install monitoring prometheus-community/kube-prometheus-stack --version 92.10.1 --namespace monitoring --create-namespace -f monitoring/values.yaml

## Verification

Check monitoring pods:

    minikube kubectl -- -n monitoring get pods

Check ServiceMonitors:

    minikube kubectl -- -n monitoring get servicemonitors

## Access Grafana

Start port forwarding from the EC2 host:

    minikube kubectl -- -n monitoring port-forward svc/monitoring-grafana 3000:80

Keep port forwarding running. From a Windows workstation, create an SSH tunnel to the EC2 host and open http://localhost:3000 in a browser.

Use the Grafana admin account. Never store the admin password in this repository.

## Dashboard and Metrics

The Kubernetes / Compute Resources / Cluster dashboard was used to view:

- CPU utilisation and CPU requests/limits
- Memory utilisation and memory requests/limits
- Namespace-wise CPU usage
- Network and storage I/O panels

## Troubleshooting

Check pod readiness and restart counts:

    minikube kubectl -- -n monitoring get pods

Check recent monitoring events:

    minikube kubectl -- -n monitoring get events --sort-by=.lastTimestamp

If a panel shows No data, check the dashboard time range, Prometheus targets, and availability of the required metrics.

If port forwarding reports lost connection to pod, check the pod status and Minikube status before reconnecting.

## Security Notes

- Do not commit passwords, tokens, private keys, kubeconfig files, or real Kubernetes Secret values.
- Use SSH tunnelling for private Grafana access.
- Review EC2 security group rules before publishing the application or Jenkins.
