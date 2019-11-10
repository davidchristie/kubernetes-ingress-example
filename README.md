# Kubernetes Ingress Example

Copied from https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/

## Minikube

### Enable the Ingress controller

1. To enable the NGINX Ingress controller, run the following command:

```console
minikube addons enable ingress
```

2. Verify that the NGINX Ingress controller is running

```console
kubectl get pods -n kube-system
```

### Deploy a hello, world app

1. Create a Deployment using the following command:

```console
kubectl run web --image=gcr.io/google-samples/hello-app:1.0 --port=8080
```

2. Expose the Deployment:

```console
kubectl expose deployment web --target-port=8080 --type=NodePort
```

3. Verify the Service is created and is available on a node port:

```console
kubectl get service web
```

4. Visit the service via NodePort:

```console
minikube service web --url
```

### Create an Ingress resource

1. Create the Ingress resource by running the following command:

```console
kubectl apply -f example-ingress.yaml
```

2. Verify the IP address is set:

```console
kubectl get ingress
```