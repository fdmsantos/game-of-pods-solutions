# Solve Redis Islands Challenge

## Create Folders on Node01

```bash
ssh node01
mkdir /redis01
mkdir /redis02
mkdir /redis03
mkdir /redis04
mkdir /redis05
mkdir /redis06
```

## Create Persistent Volumes

```bash
kubectl apply -f redis01-pv.yaml
kubectl apply -f redis02-pv.yaml
kubectl apply -f redis03-pv.yaml
kubectl apply -f redis04-pv.yaml
kubectl apply -f redis05-pv.yaml
kubectl apply -f redis06-pv.yaml
```

## Deploy Cluster and Service

```bash
kubectl apply -f redis-svc.yaml
kubectl apply -f redis.yaml 
```

## Configure Redis Cluster

```bash
kubectl exec -it redis-cluster-0 -- redis-cli --cluster create --cluster-replicas 1 $(kubectl get pods -l app=redis-cluster -o jsonpath='{range.items[*]}{.status.podIP}:6379 ') 
```