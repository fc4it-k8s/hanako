# Aws Infrastructure:
Region: Ohio us-east-2


## Installing the Charts

### Ecs-helm

```console
helm repo add ecs-helm 
kubectl create namespace ecs-helm
helm install ecs-helm  --namespace ecs-helm
```
### Prometheus

Add the repo of prometheus

```console
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
```
If needed add the namespace

```console
kubectl create namespace prometheus
```
If you did not add the namespace do not forget to remove it from the command below

```console
helm install prometheus prometheus-community/prometheus --namespace prometheus --set alertmanager.persistentVolume.storageClass="gp2" --set server.persistentVolume.storageClass="gp2"
```

### Grafana

```console
mkdir ${HOME}/environment/grafana
```
From your git clone 

```console
mv grafana.yaml ~/environment/grafana/grafana.yaml
```
Install the grafana helm
you can change the namespace, password and other parameters if needed

```console
kubectl create namespace grafana
helm install grafana grafana/grafana \--namespace grafana \--set persistence.storageClassName="gp2" \--set persistence.enabled=true \--set adminPassword='EKS!sAWSome' \--values ${HOME}/environment/grafana/grafana.yaml \--set service.type=LoadBalancer
```

### Argocd  

(command from https://github.com/argoproj/argo-helm/tree/master/charts/argo-cd )

To install the argo chart with the release name `my-release`:

```console
helm repo add argo https://argoproj.github.io/argo-helm
"argo" has been added to your repositories

helm install my-release argo/argo-cd
NAME: my-release
...
```
