# <a href='https://krossboard.app/'><img src='https://github.com/2-alchemists/krossboard/blob/master/assets/krossboard-logo.png' alt='Krossboard logo'></a>

[Krossboard](https://krossboard.app/) provides a centralized resource usage accounting & analytics for multiple Kubernetes. 

Key features:

* **Cross-cloud and cross-Kubernetes distribution**: By design, Krossboard enables to handle usage accounting and analytics across any Kubernetes distributions. It's actively tested against Amazon EKS, Microsoft AKS, Google GKE Red Hat OpenShift, Rancher RKE, vanilla Kubernetes.
* **Visualization at a central place**: Krossboard runs atop of multiple Kubernetes clusters to provide an *comprehensive and consistent usage analytics and accounting* framework. This unique feature helps organizations to set up a global strategy to understand their Kubernetes spending in order to take appropriate cost optimization decisions.
* **Deploy in minutes, for multiple clusters**: Krossboard is an integrated tool easy to deploy. Released as ready-to-install virtual machine appliances, cloud images and  binary packages, its deployment only needs a couple of minutes.
* **Consistent Accounting, for Cost allocation and Capacity planning**: Krossboard regularly collects instantaneous usage metrics, then aggregate and consolidate over time to produce short-term (hourly), mid-term (daily) and long-term (monthly) usage accouting covering up to a year. At any point or period of time, your organization can get relevant accounting insights for cost allocation and capacity planning.
* **Discovery of Managed Kubernetes clusters**:  When deployed on a supported cloud environment, Krossboard can be configured to automatically discover and track the usage of your managed Kubernetes on Amazon EKS, Google GKE and Microsoft AKS.
* **User-extensible analytics**: Krossboard enables REST API to expose the analytics data it generates to third-parties systems. Data can be exposed in JSON or CSV format.


![Krossboard Demo](./assets/krossboard-demo-v1.1.0.gif)
[![StackShare](http://img.shields.io/badge/tech-stack-0690fa.svg?style=flat)](https://stackshare.io/2alchemists/krossboard)

# Getting Started
* [Setup Krossboard for Multi-Cloud or Cross-Kubernetes Distributions](https://krossboard.app/docs/60_deploy-for-cross-cloud-and-on-premises-kubernetes/)
* [Setup Krossboard for Amazon EKS](https://krossboard.app/docs/50_deploy-for-amazon-eks/)
* [Setup Krossboard for Azure AKS](https://krossboard.app/docs/30_deploy-for-azure-aks/)
* [Setup Krossboard for Google GKE](https://krossboard.app/docs/20_deploy-for-google-gke/)

## Open to Contributions
This repository provides release packages, [scripts and built-in configuration files](tooling/setup) used to set up Krossboard.

We encourage feedback and always make our best to handle any issues as fast as possible. Don't hesitate to submit issues or feature requests.

## Useful Links
* [Open an issue or feature request](https://github.com/2-alchemists/krossboard/issues)
* [Documentation](https://krossboard.app/docs/)
* [Releases Information](https://krossboard.app/docs/releases)
