
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

When using [Trino Helm Chart](https://github.com/trinodb/charts), make sure to add JMX connector to make its catalog available.

```yaml
#...
additionalCatalogs:
  jmx: |
    connector.name=jmx
```


## Configuration

The following table lists the configurable parameters of the Bunny-metrics chart and their default values.

| Parameter                | Description             | Default        |
| ------------------------ | ----------------------- | -------------- |
| `name` |  | `"bunny-metrics"` |
| `nameOverride` | Override service name with a custom value. If not, the service name will contain Release.Name prepended with either Values.Name or Chart.Name when no duplicating. | `null` |
| `deployment.replicas` |  | `1` |
| `deployment.image` |  | `"ghcr.io/bluecatengineering/bunny-metrics:main"` |
| `deployment.imagePullPolicy` |  | `"Always"` |
| `deployment.containerPort` |  | `8090` |
| `deployment.velocityProperties` | An array of strings containing Apache Velocity [properties](https://velocity.apache.org/engine/2.0/configuration.html). Example: `- "directive.if.emptycheck = true"` | `[]` |
| `deployment.trino.host` | Host where Trino is located. Since is a sidecar, ideally it should be closest as possible. | `"localhost"` |
| `deployment.trino.port` | Port where Trino service is running. | `8080` |
| `deployment.trino.jdbcProperties.user` | By default, any value is enough here, unless security configuration has changed on Trino side. More JDBC parameters [click here](https://trino.io/docs/current/installation/jdbc.html#parameter-reference). | `"bunny-metrics"` |
| `service.port` |  | `8090` |



---
_Documentation generated by [Frigate](https://frigate.readthedocs.io)._

# Change Log

This file documents all notable changes to Bunny-Metrics Helm Chart. The release
numbering uses [semantic versioning](http://semver.org).

## v0.1.10

### Minor changes

* Fix ConfigMap name and its Deployment reference.

## v0.1.9

### Minor changes

* Fix prefixed namespace on configmap and deployment.

## v0.1.8

### Minor changes

* Update `deployment.trino.jdbcProperties.user` to "bunny-metrics" in order to differentiate from Trino UI query reports.
* Add template helper `nameOverride` to override service name and prepend Release.Name to Values.Name/Chart.Name.

## v0.1.7

### Minor changes

* Basic setup with current available metrics and Trino configuration.

