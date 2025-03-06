# k8s-mariadb-statefulset
Sample K8s configuration files for a MariaDB service as a StatefulSet setup, for reference purposes only.

## Execution order

1. Create namespace and switch.
1. Storage class.

```shell
# Create namespace
kubectl create -f app-namespace.yaml

# Switch to namespace
kubens k8s-mariadb

# Storage class.
kubectl apply -f docker-sc.yaml

``` 

## Delete all

```shell
kubens k8s-mariadb
kubectl delete all --all
kubectl delete -f docker-sc.yaml
kubens default
kubectl delete -f app-namespace.yaml
``` 

## Additional details

### For secrets

For secrets, get base64 encoded strings using:
```shell
echo -n "my string" | base64
```
