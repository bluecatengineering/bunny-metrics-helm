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

