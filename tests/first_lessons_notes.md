### 1. Start minikube (local kubernetes)
```bash
minikube start
```

This enables us to deploy pods into an existing kubernetes (it can be running on minikube or on a production cluster for these tests).

### 2. Create a `pod`

```bash
kubectl run hello-minikube \
        --image=googlecontainer/echoserver:1.4 \
        --port=8080
```

This runs a pod (consisting only on one container) to our minikube installation.
To check if it's running and the status:

```bash
kubectl get pods
```

### 3. Create the `service` 

This basically exposes a `pod`.

```bash
kubectl expose deployment \
        hello-minikube \
        --type=NodePort
```
Check the minikube URL for that service:

```bash
minikube service hello-minikube --url
```

You can now access that service on the URL this returns.


###### Notes

If you get:

```bash
Error from server (AlreadyExists): services "hello-minikube" already exists
```

You can simply delete the k8s resource with

```bash
kubectl delete service hello-minikube  
```
