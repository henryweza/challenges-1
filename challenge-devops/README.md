How to Setup and run a code
=======
1. Update a code in to Git or every where you store code

2. clone to the local to build a docker image if you edit a image please Edit in Dockerfile

3. Pre Flight a application with docker-compost for test a any bug on system
``` bash
  docker-compose up -d
```

4. if you test all function and feature in a test ENV are OK you will push a image to dockerhub to deployments
``` bash
  docker login --username
  docker image ls
  docker tag <image ID> <dockerhub username>/challenge-devops_app:latest
  docker push <dockerhub username>/challenge-devops_app:latest
```

5. After you push a image to dockerhub already please recheck by recheck list
- Change a schema
- Change a database 
- User pass database change

*IF User pass database change please add a new secret and RE-deploy a step follow a README.md in K8S/postgres/README.md and K8S/rails/README.md andd follow a *For New Setup*

*IF Change a schema or Change a database please RE-deploy for step 1 

## Choice 

[ ] For New Setup Please DO follow For new Setup  

[ ] For Update Code Please Follow For Update


### For new Setup
1. Setup a PostgreSQl in K8S Cluster Follow [Guide](https://github.com/henryweza/challenges/tree/master/challenge-devops/K8S/postgres).

2. Setup a Rail if in K8S Cluster Follow [Guide](https://github.com/henryweza/challenges/tree/master/challenge-devops/K8S/rails). for Setup a application Pod and Service for connect from external

3. Finish Enjoin a services

### For Update
1. go to K8S/rails
``` bash
cd K8S/rails/
```
2. Edit a image Version in K8S/rails/setup.yaml and K8S/rails/rails_deploy.yaml 
``` bash
vim setup.yaml

vim rails_deploy.yaml
```
3. Apply a config 

``` bash
kubectl apply -f rails_deploy.yaml
```
4. Finish Enjoin a services


