# KEDA AI SCALER 

## Overview 

KEDA AI Scaler is an open-source component that enables Kubernetes-based applications to scale based on AI model inference workloads. It leverages KEDA (Kubernetes Event-Driven Autoscaling) to monitor AI inference requests and dynamically adjust the number of pods in a deployment based on the demand for AI services.

## Features 

## Use with minikube 

### Prerequisites 
- Install [minikube](https://minikube.sigs.k8s.io/docs/start/) 
- Install [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Install [KEDA](https://keda.sh/docs/latest/install/) in your minikube cluster 
- Install [Helm](https://helm.sh/docs/intro/install/) 
- Install [Docker](https://docs.docker.com/get-docker/) 

### Steps 
1. Start minikube 
```bash
minikube start
```

2. Install KEDA 
```bash
kubectl create namespace keda
helm repo add kedacore https://kedacore.github.io/charts
helm repo update
helm install keda kedacore/keda --namespace keda
``` 
make sure `keda-operator` pod is running in `keda` namespace:
```bash
kubectl get pods -n keda
``` 
