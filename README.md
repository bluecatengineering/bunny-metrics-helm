
Bunny-Metrics (Trino sidecar) Kubernetes Helm Charts
===========
[![Release Bunny-Metrics Chart](https://github.com/bluecatengineering/bunny-metrics-helm/actions/workflows/release.yaml/badge.svg?branch=main)](https://github.com/bluecatengineering/bunny-metrics-helm/actions/workflows/release.yaml)

A sidecar to run alongside Trino to gather metrics using the JMX connector and expose them in different formats using Apache Velocity.

---

## Usage

### Requirements
* [Helm](https://helm.sh)

### Installation
Add this repo:

```shell
helm repo add bunny-metrics https://bluecatengineering.github.io/bunny-metrics-helm/
```

Install helm chart:

```shell
helm install my-bunny-metrics bunny-metrics/bunny-metrics --version 0.1.0
```