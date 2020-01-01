# Solve Pento File Server Challenge

## Fix Kube config


Edit /root/.kube/config and change server Port in cluster to 6443

## Fix kube-apiserver

```bash
# Find kube api-server container
docker ps -a 
# Check the Error
docker logs <kube-api-server-container-id> 
# The Error indicate the certificate path is wrong
ls /etc/kubernetes/pki/ # Find the correct certificate path (/etc/kubernetes/pki/ca.cert)
# Edit Kube-apiserver manifest and replace the path 
nano /etc/kubernetes/manifests/kube-apiserver.yaml
```
## Fix coredns deployment

```bash
# Edit deployment and replace the image (k8s.gcr.io/coredns:1.3.1)
kubectl edit deploy coredns -n kube-system
```

## Uncordon Node01

```bash
# To permit pods be scheduled in node01
kubectl uncordon node01
```

## Deploy Persistent Volume and Claim

```bash
kubectl apply -f data-pv.yaml
kubectl apply -f data-pvc.yaml
```
 
## Deploy File Server Deploy and Service
 
```bash
kubectl apply -f fileserver-svc.yaml
kubectl apply -f file-server.yaml
```