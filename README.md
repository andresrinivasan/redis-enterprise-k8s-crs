# Redis Enterprise K8s Custom Resources

Capture CRs to for testing and reuse

## Install the Redis Enterprise Operator

```sh
version=$(curl -s "https://api.github.com/repos/RedisLabs/redis-enterprise-k8s-docs/releases/latest" | jq -r '.name')

kubectl create namespace redis && kubectl config set-context --current --namespace=redis
kubectl apply -f https://raw.githubusercontent.com/RedisLabs/redis-enterprise-k8s-docs/v${version}/bundle.yaml
```

## Create a REC

```sh
kubectl apply -f https://github.com/andresrinivasan/redis-enterprise-k8s-custom-resources/raw/master/getting-started/rec.yaml
```

** WAIT for the REC Pods to be created **

## Create a REDB

```sh
kubectl apply -f https://github.com/andresrinivasan/redis-enterprise-k8s-custom-resources/raw/master/getting-started/redb-tls.yaml
```

## Retrieve Admin Credentials

```sh
kubectl get secrets rec-demo -o json | jq '.data[] | @base64d'
```