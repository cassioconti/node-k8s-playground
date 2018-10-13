# Node - K8s

## Docker

Build the docker image: `docker build -t cassioconti/cassionode-svc:v1 .`

Run the docker image: `docker run --name node-k8s -d -p 8080:8080 cassioconti/cassionode-svc:v1`

Access in browser: `http://<docker-machine ip>:8080`

Stop the container: `docker container stop node-k8s`

Remove the container: `docker container rm node-k8s`

Remove docker image: `docker image rm cassioconti/cassionode-svc:v1`

### Useful commands

Get the container IP address: `docker-machine ip`

If you need to connect to the container: `docker exec -it node-k8s /bin/bash`

See running containers: `docker ps`

List docker images: `docker image ls`

Push local docker image to registry: `docker push cassioconti/cassionode-svc:v1`

## GCloud

Create a fixed IP address: `gcloud compute addresses create cassio-cf`

## Kubernetes

Create the namespace: `kubectl apply -f ./k8s/namespace.yaml`

Create the secret: `kubectl create secret tls cassio-cf --key ./letsencrypt/key.txt --cert ./letsencrypt/cert.txt -n services`

Delete the secret: `kubectl delete secret cassio-cf -n services`

Create the deployment: `kubectl apply -f ./k8s/deployment.yaml`

Create the service: `kubectl apply -f ./k8s/service.yaml`

Create the ingress: `kubectl apply -f ./k8s/ingress.yaml`

### Useful commands

`kubectl get event`

`kubectl get service`

`kubectl get deployment`

`kubectl get pod`

`kubectl get node`