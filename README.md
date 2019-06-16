### Sandbox for Helm

Helm is a package manager for kubernetes objects

A good package manager provides
- Automated installation
    - `helm install ...`
- Version control
    - `helm upgrade ...`
- Dependency management
    - `helm dep list|update`
    - `helm repo ...`
- Automated removal
    - `helm delete`

### Installation

- `brew install kubernetes-helm`
- `helm init`

### Concepts

- Helm chart: a collection of Kubernetes objects that run together for a full application


### Notes

- Tiller runs inside kubernetes and manages releases of the charts. 

### Installing charts

- `helm ls`
- `helm search wordpress`
- `helm install stable/wordpress`
- `helm install stable/wordpress --version 5.0.1`
- `helm upgrade <release-name> stable/wordpress`
- `helm delete <release-name>`

### Looking at charts

- `helm fetch --untar stable/wordpress`
- `helm dep list`
- `helm dep update`

### Helm repositories

Official repository: https://kubernetes-charts.storage.googleapis.com

Needs an index.yaml file

Can use a Cloud Storage Provider. e.g. S3, GCP Container... Any place capable of serving the index YAML file.

You can create your own charts locally
- `helm create <chart-name>`
- `helm fetch`