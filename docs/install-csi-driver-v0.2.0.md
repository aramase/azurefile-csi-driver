# Install azurefile CSI driveri v0.2.0-alpha on a kubernetes cluster

If you have already installed Helm, you can also use it to install azurefile CSI driver. Please see [Installation with Helm](../charts/README.md).

## Installation with kubectl

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/azurefile-csi-driver/master/deploy/v0.2.0/crd-csi-driver-registry.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/azurefile-csi-driver/master/deploy/v0.2.0/crd-csi-node-info.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/azurefile-csi-driver/master/deploy/v0.2.0/rbac-csi-azurefile-controller.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/azurefile-csi-driver/master/deploy/v0.2.0/csi-azurefile-controller.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/azurefile-csi-driver/master/deploy/v0.2.0/csi-azurefile-node.yaml
```

- check pods status:

```
watch kubectl get po -o wide -n kube-system | grep csi-azurefile
```

example output:

```
NAME                                            READY   STATUS    RESTARTS   AGE     IP             NODE
csi-azurefile-controller-56bfddd689-dh5tk       6/6     Running   0          35s     10.240.0.19    k8s-agentpool-22533604-0
csi-azurefile-node-cvgbs                        3/3     Running   0          7m4s    10.240.0.35    k8s-agentpool-22533604-1
csi-azurefile-node-dr4s4                        3/3     Running   0          7m4s    10.240.0.4     k8s-agentpool-22533604-0
```

- clean up azure file CSI driver

```
kubectl delete -f https://raw.githubusercontent.com/kubernetes-sigs/azurefile-csi-driver/master/deploy/v0.2.0/csi-azurefile-controller.yaml
kubectl delete -f https://raw.githubusercontent.com/kubernetes-sigs/azurefile-csi-driver/master/deploy/v0.2.0/csi-azurefile-node.yaml
kubectl delete -f https://raw.githubusercontent.com/kubernetes-sigs/azurefile-csi-driver/master/deploy/v0.2.0/crd-csi-driver-registry.yaml
kubectl delete -f https://raw.githubusercontent.com/kubernetes-sigs/azurefile-csi-driver/master/deploy/v0.2.0/crd-csi-node-info.yaml
kubectl delete -f https://raw.githubusercontent.com/kubernetes-sigs/azurefile-csi-driver/master/deploy/v0.2.0/rbac-csi-azurefile-controller.yaml
```
