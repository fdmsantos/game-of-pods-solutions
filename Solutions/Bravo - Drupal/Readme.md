# Deploy

## Create Folders on Node01

```bash
ssh node01
mkdir /drupal-data
mkdir /drupal-mysql-data
```


## Deploy Persistent Volumes and Persistent Volumes Claim

```bash
kubectl apply -f drupal-pv.yaml
kubectl apply -f drupal-pvc.yaml
kubectl apply -f drupal-mysql-pv.yaml
kubectl apply -f drupal-mysql-pvc.yaml
```

## Deploy Secret

```bash
kubectl create secret generic drupal-mysql-secret --from-literal=MYSQL_ROOT_PASSWORD=root_password --from-literal=MYSQL_DATABASE=drupal-database --from-literal=MYSQL_USER=root
```

## Deploy Drupal and Mysql

```bash
kubectl apply -f drupal-mysql.yaml
kubectl applt -f drupal.yaml
```

## Deploy Services

```bash
kubectl expose deploy drupal-mysql --name=drupal-mysql-service --type=ClusterIP --target-port=3306
kubectl apply -f drupal-svc.yaml
```


