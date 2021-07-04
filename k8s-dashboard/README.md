# Deploying the Kubernetes Dashboard
The files in this folder are for deploying the kubernetes dashboard into the cluster.

```sh
# Deploy the Kubernetes dashboard
kubectl apply -f recommended.yaml

# Create an administrator service account with a bearer token
kubectl apply -f admin-account.yaml

# Retrieve the bearer token
kubectl -n kubernetes-dashboard get secret $(kubectl -n kubernetes-dashboard get sa/admin-user -o jsonpath="{.secrets[0].name}") -o go-template="{{.data.token | base64decode}}"
```

Log in to the dashboard:

`https://<cluster-node-ip>:30443`

Select **Token** and paste the token into the text field.