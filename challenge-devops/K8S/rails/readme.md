# Requirement

1. Build a Image and push to docker hub already
2. Setup Postgre Database is Success Already
3. Confirm a Secret user and pass of database is a same in application


## Step for Setup to run a Rail Service on K8S Cluster 

1. Prepare a Database for Rail Because some developer are setup a schema tables or index in a database with K8S Jobs

```bash
kubectl create -f setup.yaml 
```

2. check a job status is success

```bash
kubectl get jobs 
```

3. are job is success to setup a database you can deploy a Rail pod in to K8S Cluster

```bash
kubectl create -f rails_deploy.yaml
```

4. and run a rail Service for allow Connection from external can access a Rail Pods
```bash
kubectl create -f rails_svc.yaml
```

5.Confirm a all pod & service run 
```bash
kubectl get svc,pod,deployments
```
## Mentions
if you want to change a password please create a new secret because you can change back after fail or can't remember a old user pass

Sample
* Create a new user and password secret for database is point to change in rails_deploy.yaml and setup.yaml

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
