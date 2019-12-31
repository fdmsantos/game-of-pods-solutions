# Solve Voting Application Challenge

## Create namespace vote

```bash
kubectl create ns vote
```

## Deploy Vote App

```bash
kubectl apply -f vote.yaml
kubectl apply -f vote-svc.yaml
```

## Deploy Redis

```bash
kubectl apply -f redis.yaml
kubectl apply -f redis-svc.yaml
```

## Deploy DB

```bash
kubectl apply -f db.yaml
kubectl apply -f db-svc.yaml
```

## Deploy Result App 

```bash
kubectl apply -f result.yaml
kubectl apply -f result-svc.yaml
```

## Deploy Worker

```bash
kubectl apply -f worker.yaml
```
