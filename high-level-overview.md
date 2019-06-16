# High Level Overview of Helm and Tiller

Helm has two parts:
- Helm client
- Tiller server
    - lives in the kube-system namespace
    - This server listens for helm client requests

### Helm

Helm uses kubectl to talk to Tiller.

### Tiller

Tiller runs as a Pod in Kubernetes on the kube-system namespace. 
It manages the releases installed on it.

Naming: 
- charts
- config
- release

# Where do you get the charts?

Helm looks for charts in `~/.helm/repository/repository.yaml`

The index file is cached. You need to update it every now and then. 

## Commands

- `helm repo add`
- `helm repo update`