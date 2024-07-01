# Server Side Apply

## Example

Suppose we have an example Deployment `deployment.yaml` with contents:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: my-nginx
  name: my-nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: my-nginx
  template:
    metadata:
      labels:
        app: my-nginx
    spec:
      containers:
      - image: nginx
        name: nginx
```

Use Server-Side Apply:

```sh
kubectl apply -f deployment.yaml --server-side --field-manager=andy
```

Retrieve managed fields:

```sh
kubectl get deploy my-nginx -o yaml --show-managed-fields
```

Reference
<https://kubernetes.io/docs/reference/using-api/server-side-apply/>
