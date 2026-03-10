# Monitoring and Logging

## Overview

This project uses Prometheus and Grafana for application monitoring.

The backend exposes a Prometheus-compatible metrics endpoint at `/metrics`.

Metrics currently exposed include:

- `mongo_connection_status` — MongoDB connection health
- `expenses_total` — total number of expense documents
- `http_requests_overall_total` — overall total HTTP request count
- `http_requests_total` — HTTP request count by method, route, and status code

## Prometheus

Prometheus scrapes the backend metrics endpoint.

Configuration file:

- `monitoring/prometheus.yml`

During local testing, Prometheus is run in Docker and scrapes the backend through the local port-forwarded backend service.

## Grafana

Grafana is used to visualize the metrics collected by Prometheus.

Dashboard file:

- `monitoring/grafana-dashboard.json`

Dashboard panels include:

- MongoDB connection status
- total expenses
- overall HTTP requests
- HTTP requests by route and status

## Logging

Application logs are written to stdout/stderr by the containers.

Kubernetes captures these logs automatically.

Logs can be viewed with:

```bash
kubectl logs deployment/backend -n student-prince
kubectl logs deployment/frontend -n student-prince