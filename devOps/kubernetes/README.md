# List Command

- delete all deployments -> run `kubectl delete deployments --all`
- delete all pods -> run `kubectl delete pods --all`
- get all data  -> run `kubectl get all`
- get context list -> run `kubectl config get-contexts`
- get cluster info -> run `kubectl cluster-info`

# Quick Setup 

## KinD (kubernetes in Docker)

- create cluster `kind create cluster --config kind-example-config.yml --name my-cluster`
- delete cluster `kind delete cluster --name my-cluster`
- sample kind-example-config.yml
  ```
  kind: Cluster
  apiVersion: kind.x-k8s.io/v1alpha4
  nodes:
  - role: control-plane
  - role: worker
  - role: worker
  - role: worker
  ```

## Minikube
