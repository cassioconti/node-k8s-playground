# Node - K8s

## Docker

Build the docker image: `docker build -t cassioconti/node-k8s:v1 .`

Run the docker image: `docker run --name node-k8s -d -p 8080:8080 cassioconti/node-k8s:v1`

Access in browser: `http://<docker-machine ip>:8080`

Stop the container: `docker container stop node-k8s`

Remove the container: `docker container rm node-k8s`

Remove docker image: `docker image rm cassioconti/node-k8s:v1`

### Useful commands

Get the container IP address: `docker-machine ip`

If you need to connect to the container: `docker exec -it node-k8s /bin/bash`

See running containers: `docker ps`

List docker images: `docker image ls`

Push local docker image to registry: `docker push cassioconti/node-k8s:v1`

## Kubernetes

Run image in cluster: `kubectl run node-k8s --image=cassioconti/node-k8s:v1 --port=8080`

Expose through a service: `kubectl expose deployment node-k8s --type=LoadBalancer`

Set a different image: `kubectl set image deployment/node-k8s node-k8s=cassioconti/node-k8s:v2`

Remove the service: `kubectl delete service node-k8s`

Remove the deployment: `kubectl delete deployment node-k8s`

### Useful commands

`kubectl get event`

`kubectl get service`

`kubectl get deployment`

`kubectl get pod`

`kubectl get node`