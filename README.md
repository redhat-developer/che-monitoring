# Monitoring Eclipse Che with Prometheus

This repository provides an opinionated way of monitoring Eclipse Che with Prometheus

A full guide on the functionality is available here: https://www.eclipse.org/che/docs/che-7/monitoring-che.html

This repository includes:
- An OpenShift template to set up a Prometheus instance that monitors Che-Server in the same namespace as itself

## Usage: 

- Create a configmap for the Prometheus scrape config as referenced in the Deployment spec
- Process the OpenShift template, supplying the IMAGE and IMAGE_TAG parameters
- `oc create` the template
- Create a Route for your new Prometheus instance
- Add this Prometheus instance as a datasource in Grafana
- With your preferred workflow, add the dashboards to your Grafana instance

You now have operational insights and metrics for Eclipse Che! 
