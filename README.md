[![lint](https://img.shields.io/github/actions/workflow/status/2-alchemists/krossboard-kubernetes-operator/lint.yml?label=Lint&style=for-the-badge&logo=github)](https://github.com/2-alchemists/krossboard-kubernetes-operator/actions/workflows/lint.yml)
![license](https://img.shields.io/github/license/2-alchemists/krossboard-kubernetes-operator.svg?label=License&style=for-the-badge)

---

<!-- vscode-markdown-tkubectl -->
- [What is Krossboard](#what-is-krossboard)
- [Deploy Krossboard](#deploy-krossboard)
- [Create a Krossboard Instance](#deploy-a-krossboard-instance)
  - [Create a Krossboard CR](#create-a-krossboard-cr)
  - [Create a KUBECONFIG secret for target Kubernetes](#create-a-kubeconfig-secret-for-target-kubernetes)
  - [Start the Krossboard Instance](#start-the-krossboard-instance)
- [Day2 Operations](#day2-operations)

<!-- vscode-markdown-toc-config
	numbering=false
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-tkubectl -->

# What is Krossboard

Krossboard is a Kubernetes Operator designed to provide comprehensive usage tracking, analytics, and accounting across diverse Kubernetes environments. It supports cross-site deployments (e.g., geographically dispersed clusters) and cross-distribution management (e.g., vanilla Kubernetes, OpenShift, EKS, AKS, GKE, and other distributions).

Krossboard enables enterprises to gain insights into resource consumption, perform cost analysis, and centralize monitoring across multiple Kubernetes clusters. For example, it helps manage resource usage across multiple cloud providers and provides detailed cost analysis for hybrid deployments. Check out the documentation for more details.

![](krossboard-architecture-overview.png)


Once the Operator installed, the [Krossboard CR](https://raw.githubusercontent.com/2-alchemists/krossboard-kubernetes-operator/main/config/releases/latest/krossboard/krossboard-kubernetes-operator.yaml) allows to define a Krossboard instance as a Kind, as well as parameters to bootstrap that instance: krossboard-api, krossboard-ui, krossboard-consolidator, krossboard-kubeconfig-handler, kube-opex-analytics instances.

Each instance of Krossboard enables to track the usage of a set of Kubernetes clusters listed in a KUBECONFIG secret.

The next steps describe how to deploy the operator and a Krossboard instance.

> Learn more about [Krossboard Features](./docs/what-is-krossboard.md)

# <a name='DeployKrossboardOperator'></a>Deploy Krossboard
The following command deploy the latest version of Krossboard Operator.

```bash
kubectl apply -f https://raw.githubusercontent.com/2-alchemists/krossboard-kubernetes-operator/main/config/releases/latest/krossboard/krossboard-kubernetes-operator.yaml
```

The installation is achieved in a namespace named `krossboard`.

# <a name='DeployaKrossboardInstance'></a>Deploy a Krossboard Instance

## <a name='CreateaKrossboardCR'></a>Create a Krossboard CR

Once the operator deployed, a custom resource named `Krossboard` is created. This CR is used to define each instance of Krossboard.

See [krossboard.yaml](https://github.com/2-alchemists/krossboard-kubernetes-operator/blob/main/config/releases/latest/krossboard/krossboard.yaml) for an example to a Krossboard instance along with its persistent volume claim.

```yaml
---
apiVersion: krossboard.krossboard.app/v1alpha1
kind: Krossboard
metadata:
  name: krossboard
  namespace: krossboard
spec:
  koaImage: rchakode/kube-opex-analytics:25.03.1
  krossboardDataProcessorImage: krossboard/krossboard-data-processor:1.3.0
  krossboardUIImage: krossboard/krossboard-ui:1.2.2-d49718c
  krossboardPersistentVolumeClaim: krossboard-data-pvc
  krossboardSecretName: krossboard-secrets
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: krossboard-data-pvc
  namespace: krossboard
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
#  storageClassName: uncomment-and-set-if-not-using-default
```

Each instance of Krossboard allows to track the usage of a set of Kubernetes clusters listed in a KUBECONFIG secret. 

* The secret name is set by the parameter `krossboardSecretName` (default is `krossboard-secrets`).
* The secret key is `kubeconfig`. 

## <a name='CreateaKUBECONFIGsecretfortargetKubernetes'></a>Create a KUBECONFIG secret for target Kubernetes
Given a KUBECONFIG resource (`/path/to/kubeconfig` in the below command), you can create a secret for Krossboard Operator as follows. 

```bash
kubectl -n krossboard \
    create secret --type=Opaque generic krossboard-secrets \
    --from-file=kubeconfig=/path/to/kubeconfig
```

> * Learn how to [Create a KUBECONFIG resource with minimal permissions for Krossboard](./docs/create-kubeconfig-with-minimal-permissions.md).
> * Learn how to [Create a secret from several KUBECONFIG resources](./docs/create-kubeconfig-secret.md)


## <a name='StarttheKrossboardInstance'></a>Start the Krossboard Instance
The below command deploys an instance of Krossboard based on the latest version.

```bash
kubectl -n krossboard apply -f https://raw.githubusercontent.com/2-alchemists/krossboard-kubernetes-operator/main/config/releases/latest/krossboard/krossboard-deployment.yaml
```

Once started, the instance enables access to two Kubernetes services:

* `krossboard-ui.krossboard.svc` enabling access to Krossboard UI.
* `krossboard-api.krossboard.svc` enabling access to Krossboard REST API.

# Day2 Operations

* https://krossboard.app/
* [Krossboard Enterprise Support](https://krossboard.app/#pricing) 
