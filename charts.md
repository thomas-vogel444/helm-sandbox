# Helm Charts

### What are charts?

It is a directory were all the resources are defined that are deployed in an application.

It contains:
- Chart.yaml: metadata about the chart
- requirements.yaml: File listing of the dependencies
- values.yaml: where template values are defined. Note that dependencies values.yaml file will override the values in the parent Chart directory.
- templates/: templatised Kubernetes resources which Helm will deploy

Charts are templatised and initiliased at install time.

### Cutomising charts

3 ways to customise charts:
    1) Override values one time during the install command
    2) fetch the chart and modify the values file
    3) pass a values.yaml file on the install command line to override some values
        - e.g. `helm install --values=.valuesstore/whatever.yaml stable/wordpress`

### Create a custom chart

Use `helm create <chart-name>` and modify the chart directory

### Repositories

Places where you store your charts! 

Any HTTP server serving files with an index.yaml, e.g. S3, Github, custom web server. Use `helm repo index .`

The repository expects tgz files. You can package charts using `helm package <chart-name>`

Add the repo to helm: `helm repo add <repo-name> <repo-url>` 
E.g. `helm repo add personal https://raw.githubusercontent.com/thomas-vogel444/personal-helm-repository/master/`

### Releases

- Install a specific version of a chart: `helm install --version=5.2.2 stable/process`
- Change the version number in `Chart.yaml` and run `helm package <chart-name>`
- Update the index: `helm index .`
- Update the local cache: `helm repo update`
- Upgrade app version in Kubernetes: `helm upgrade --recreate-pods <release-name> <chart-name>`

Questions: 
- There are 2 versions in Chart.yaml: appVersion and version. Which is which?
    - version is the chart version.
    - appVersion: ???