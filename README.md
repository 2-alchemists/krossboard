![](krossboard-architecture-overview.png)

- [Overview](#overview)
- [Getting Started](#getting-started)
- [Open to Contributions](#open-to-contributions)

--- 
 
# Overview
Krossboard provides an advanced & centralized resource usage analytic and accounting for multiple Kubernetes. The Kubernetes clusters can be on premises and/or in the cloud, self-deployed or managed.

Key features:

* **Multi-Kubernetes Data Collection**: Krossboard periodically collects raw metrics related to containers, pods and nodes from each Kubernetes cluster it handles. The built-in data collection period is 5 minutes.
* **Powerful Analytics Processing**: Krossboard internally processes raw metrics to produce insightful Kubernetes usage accounting and analytics metrics. The analytics data are tracked on a hourly-basis, per namespace, per cluster, and globally.
* **Insightful Usage Accounting**: Krossboard periodically processes usage accounting, per namespace and per cluster. By the default, the UI displays accounting the following periods without any additioanl configuration: daily accounting for the last 14 days, monthly for the ast 12 months.
* **REST API**: This exposes the generated analytics data it generates to third-party systems.
* **Easy to deploy**: The Krossboard operator is deployable in a couple of minutes.
* **Extensible analytics/reports**: Krossboard enables REST API to expose the analytics data it generates to third-parties analytics systems in CSV or JSON format.


![Krossboard Demo](./assets/krossboard-demo-v1.1.0.gif)

# Getting Started
* [Setup Krossboard for Multi-Cloud or Cross-Kubernetes Distributions](https://krossboard.app/docs/60_deploy-for-cross-cloud-and-on-premises-kubernetes/)
* [Setup Krossboard for Amazon EKS](https://krossboard.app/docs/50_deploy-for-amazon-eks/)
* [Setup Krossboard for Azure AKS](https://krossboard.app/docs/30_deploy-for-azure-aks/)
* [Setup Krossboard for Google GKE](https://krossboard.app/docs/20_deploy-for-google-gke/)

# Open to Contributions
This repository provides release packages, [scripts and built-in configuration files](tooling/setup) used to set up Krossboard.

We encourage feedback and always make our best to handle any issues as fast as possible. Don't hesitate to submit issues or feature requests.

[![StackShare](http://img.shields.io/badge/tech-stack-0690fa.svg?style=flat)](https://stackshare.io/2alchemists/krossboard)

