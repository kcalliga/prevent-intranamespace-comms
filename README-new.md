# Block Communications Between Pods in the Same Namespace

This repository demonstrates how to block communications between pods in the same namespace within OpenShift or Kubernetes. It includes the creation of deployments, network policies, and testing connectivity between pods.

## Prerequisites

Before you start, make sure you have:

- A Kubernetes/OpenShift cluster running.
- `oc` or `kubectl` command-line tools configured to interact with your cluster.

## Steps to Block Communications Between Pods in the Same Namespace

### 1. Create Deployments

If your namespace/project already exists, follow the steps below.

1. Inside your existing namespace, create two deployments: one for a simple HTTP server and another for network tools.

```bash
oc apply -f http-pod.yaml
oc apply -f network-tool-pod.yaml

### 2. Create Network Policies
Next, create two network policies to control traffic between pods within the same namespace.
```

oc apply -f allow-from-api-network-policy.yaml
oc apply -f allow-from-ingress-network-policy.yaml
