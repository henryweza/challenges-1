# Prepare

Pleaase read this befor run a postgres Deployments Service and Volumes 
is a setup a secret in K8S for reference to auto insert user password or everything else

## Create a Secret Key

Create a database Secret key for user and password to binding a information in the deployment file

```bash
kubectl create secret generic db-user --from-literal=username=<username!!!>
kubectl create secret generic db-user-pass --from-literal=password=<password!!!>
```


## Step for prepare a database pod and service

1. apply a postgres_volumes.yaml config file to create PV and PVC for Database

```bash
kubectl apply -f postgres_volumes.yaml 
```

2. apply a postgres_svc.yaml config file to create Service for Database

```bash
kubectl apply -f postgres_svc.yaml
```

3. apply a postgres_deploy.yaml config file to create pod of Database service 

```bash
kubectl apply -f postgres_deploy.yaml
```

4. Check a pv pvc service and deployments are up all

```bash
kubectl get pv,pvc,svc,pod,deployments
```
## Mentions
if you want to change a password please create a new secret because you can change back after fail or can't remember a old user pass


Sample
* Create a new user and password secret for database is point to change in postgres_deployments.yaml

```bash
 - name: POSTGRES_USER
          valueFrom:
            secretKeyRef:
              name: "db-user" << Change this a new secret key name
              key: "username" << Change this a new secret key values
        - name: POSTGRES_PASSWORD
          valueFrom:
            secretKeyRef:
              name: "db-user-pass" << Change this a new secret key name 
              key: "password" << Change this a new secret key values

```
