# Service-Mesh-in-action
Here we explain about basic release and deployment strategies and how powerful is service mesh to minimise the drawbacks of Microservices architectures using Kubernetes and Istio

https://medium.com/@rahul.omar/deployment-tranquility-service-mesh-sidecar-patterns-12e97a5758f4

# Setting up istio

```
gcloud container clusters get-credentials standard-cluster-1 --zone=XXX

kubectl create namespace istio-sample

curl -L https://git.io/getLatestIstio | ISTIO_VERSION=1.2.2 sh -

cd istio-1.2.2

for i in install/kubernetes/helm/istio-init/files/crd*yaml; do kubectl apply -f $i; done

helm template install/kubernetes/helm/istio --name istio --set global.mtls.enabled=false --set tracing.enabled=true --set kiali.enabled=true --set grafana.enabled=true --namespace istio-system > istio.yaml

kubectl apply -f istio.yaml

kubectl label namespace default istio-injection=enabled
```
