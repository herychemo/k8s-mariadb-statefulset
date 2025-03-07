# k8s-mariadb-statefulset
Sample K8s configuration files for a MariaDB service as a StatefulSet setup, for reference purposes only.

## Execution order

1. Create namespace and switch.
1. Storage class.
1. MariaDB Config Maps.
1. MariaDB Secrets.
1. MariaDB StatefulSet and Service.

```shell
# Create namespace
kubectl create -f app-namespace.yaml

# Switch to namespace
kubens k8s-mariadb

# Storage class.
kubectl apply -f docker-sc.yaml

# MariaDB Config Maps.
kubectl apply -f mariadb-configmap.yaml
kubectl apply -f mariadb-config-configmap.yaml
kubectl apply -f mariadb-sql-configmap.yaml
kubectl apply -f mariadb-scripts-configmap.yaml

# MariaDB Secrets.
kubectl apply -f mariadb-secret.yaml

# MariaDB StatefulSet and Service.
kubectl apply -f mariadb.yaml
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

## References
* https://kubernetes.io/docs/tutorials/stateful-application/basic-stateful-set/
* https://mariadb.com/kb/en/replication-overview/
* https://mariadb.com/kb/en/setting-up-replication/
* https://mariadb.org/mariadb-k8s-how-to-replicate-mariadb-in-k8s/
