# spot-kyverno-demo
Unlock compute saving on AKS with spot nodes and Kyverno

## Pre-requisites
1. An AKS cluster
2. A Spot node pool

## Instructions
1. Install the cluster autoscaler priority expander
    ```
    kubectl apply -f cluster-autoscaler-priority-expander.yaml
    ```
1. Install Kyverno
    ```
    helm repo add kyverno https://kyverno.github.io/kyverno/
    helm install kyverno kyverno/kyverno -n kyverno --create-namespace
    ```
1. Deploy kyverno policy
    ```
    kubectl apply -f kyverno-policy.yaml
    ```
1. After all kyverno components are deployed and ready, deploy test pods
    ```
    kubectl apply -f spot-deploy.yaml
    ```
