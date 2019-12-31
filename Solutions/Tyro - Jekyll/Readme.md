# Solve Tyro Challenge

## Deploy Persistent Volume Claim

```bash
kubectl apply -f jekyll-pvc.yaml
```

## Deploy Application and Service

```bash
kubectl apply -f jekyll.yaml
kubectl apply -f jekyll-svc.yaml
```

## Deploy Role and RoleBinding

```bash
kubectl apply -f role.yaml
kubectl apply -f rolebinding.yaml
```

## Configure user Drogo in Kube config

```bash
# Edit Kube config
nano /root/.kube.config
```

```yaml
contexts: # Add the following context
- context:
    cluster: kubernetes
    user: drogo
  name: developer
users: # Add the following user
- name: drogo
  user:
    client-key: /root/drogo.key
    client-certificate: /root/drogo.crt
```

## Switch to developer Context


```bash
kubectl config use-context developer
```
