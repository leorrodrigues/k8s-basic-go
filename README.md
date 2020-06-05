# K8S First apps
In this repo are 3 apps built to run in [Kubernetes](https://kubernetes.io/pt/).

1- A nginx app that has a configmap to change the default main page of nginx, a load balancer for Kubernetes, and the deployment pods.

2- MySQL app that contains a persistent volume, configured with Kubernetes secrets.

3- A go server containing the deployment and load balancer for Kubernetes. The docker image generated in this app is passed by a CI pipeline in the [Cloud Builder](https://cloud.google.com/cloud-build) and if its everything fine with the image then the Cloud Builder pushed the image into [dockerhub repo](https://hub.docker.com/repository/docker/leorrodrigues/go-server).

## Usage

To use these apps you need the [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) and [minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/) installed in your own machine.

To run the nginx image execute:
```bash
kubectl apply -f nginx/configmap.yaml
kubectl apply -f nginx/service.yaml
kubectl apply -f nginx/deployment.yaml
minikube service nginx-service
```

For the MySQL app:
To run the nginx image execute:
```bash
kubectl apply -f mysql/persistentVolume.yaml
kubectl apply -f mysql/deployment.yaml
```

And finally, to execute the Go webserver:
```bash
kubectl apply -f goServer/loadBalancer.yaml
kubectl apply -f goServer/deployment.yaml
minikube service go-service
```
