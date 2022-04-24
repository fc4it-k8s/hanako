# Aws Infrastructure:
Region: Ohio us-east-2


## Installing the Charts

### Ecs-helm

### Prometheus

Add the repo of prometheus

```console
$ helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```
If needed add the namespace

```console
$ kubectl create namespace prometheus
```
If you did not add the namespace do not forget to remove it from the command below

```console
$ helm install prometheus prometheus-community/prometheus --namespace prometheus --set alertmanager.persistentVolume.storageClass="gp2" --set server.persistentVolume.storageClass="gp2"
```

### Grafana
```console

```

### Argocd  

(command from https://github.com/argoproj/argo-helm/tree/master/charts/argo-cd )

To install the argo chart with the release name `my-release`:

```console
$ helm repo add argo https://argoproj.github.io/argo-helm
"argo" has been added to your repositories

$ helm install my-release argo/argo-cd
NAME: my-release
...
```
