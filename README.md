[![Build Status](https://ci.centos.org/buildStatus/icon?job=devtools-che-monitoring-build-master)](https://ci.centos.org/job/devtools-che-monitoring-build-master)

# Monitoring Eclipse Che with Prometheus

[![Contribute](https://che.openshift.io/factory/resources/factory-contribute.svg)](https://che.openshift.io/f?url=https://github.com/redhat-developer/che-monitoring)

This repository provides an opinionated way of monitoring Eclipse Che with Prometheus.

A full guide on the functionality is available here: https://www.eclipse.org/che/docs/che-7/monitoring-che.html

This repository includes:
- An OpenShift template to set up a Prometheus instance that monitors Che-Server in the same namespace as itself.

## Usage: 

- Create a configmap for the Prometheus scrape config as referenced in the Deployment spec
- Process the OpenShift template, supplying the IMAGE and IMAGE_TAG parameters.  Note that the Prometheus instance configured requires a PersistentVolume and you're expected to have dynamic storage provisioning. If you don't, just remove the reference to the `PersistentVolumeClaim` object from the template before doing an `oc process`
- `oc create` the template: `oc process -f template.yaml | oc create -f -`
- Create a Route for your new Prometheus instance
- Add this Prometheus instance as a datasource in Grafana
- With your preferred workflow, add the dashboards to your Grafana instance

You now have operational insights and metrics for Eclipse Che!
