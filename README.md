# Kubernetes Ingress Controller for OCI

Creates an Nginx Ingress controller using Nginx on OCI, using the Nginx official Ingress, modified for OCI with one command installation: https://github.com/nginxinc/kubernetes-ingress 

Creating an Ingress controller on OCI is as simple as checking out this repo and running:

```
kubectl apply -f config/
```

This will get you:

* A Service Account and Namespace for Ingress
* RBAC configuration
* A default self-signed SSL token. (Change these in \_3-secret.yaml if this is to be used in Production.)
* An Nginx-based Ingress Controller
* An OCI Load Balancer automatically provisioned.

Once applied, you can find the OCI LB IP by running:

```
kubectl describe svc nginx-ingress
```

You'll either see the public LB IP under "LoadBalancer Ingress", or you'll see a relevant error message from OCI in Events.

