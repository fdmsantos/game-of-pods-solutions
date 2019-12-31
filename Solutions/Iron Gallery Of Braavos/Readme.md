# Solve Irong Gallery of Braavos Challenge

## Deploy Iron DB

```bash
kubectl apply -f iron-db.yaml
kubectl apply -f iron-db-svc.yaml
```

## Deploy Iron Gallery

```bash
kubectl apply -f iron-gallery.yaml
kubectl apply -f iron-gallery-svc.yaml
```

## Deploy Network Policy And Ingress

```bash
kubectl apply -f network-policy.yaml
kubectl apply -f ingress.yaml
```
