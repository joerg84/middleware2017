# Exercise 4 - Installing Istio

### Clean up
 
Start with a clean slate by deleting all bookinfo from the cluster.

```sh
kubectl delete service productpage-np
cd /tmp/istio-0.2.12/samples/bookinfo/kube/
kubectl delete -f bookinfo.yaml
```

### Install Istio on the Kubernetes cluster

The tutorial environment already includes the Istio client and the Istio infrastructure deployment files.
If you do not have the client, follow the download instructions at https://github.com/szihai/istio-workshop/blob/master/exercise-5/README.md

### Install Istio on the Kubernetes cluster.

```sh
kubectl apply -f /tmp/istio.yaml # Replacement for install/kubernetes/istio.yaml with modifications
```

### Install Add-ons for Grafana, Prometheus, and Zipkin

```sh
cd /tmp/istio-0.2.12
kubectl apply -f install/kubernetes/addons/zipkin.yaml
kubectl apply -f install/kubernetes/addons/grafana.yaml
kubectl apply -f install/kubernetes/addons/prometheus.yaml
kubectl apply -f install/kubernetes/addons/servicegraph.yaml
```

### View the Istio system deployments

Istio is deployed in a separate Kubernetes namespace _istio-system_.

```sh
kubectl get pods --all-namespaces
kubectl get services --all-namespaces
```

You can also view the Istio pods in the web UI being proxied to http://localhost:8001/ui .  Select
'istio-system' from the drop-down combo box *Namespace*.

![Kubernetes Web UI](kubernetes.png)


#### [Continue to Exercise 5 - Deploying a microservice application with Istio Proxies](../exercise-5/README.md)