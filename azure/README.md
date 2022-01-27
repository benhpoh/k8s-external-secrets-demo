# Initial set up

## Install external secrets deployment

```
helm repo add external-secrets https://charts.external-secrets.io

helm install external-secrets \
   external-secrets/external-secrets \
    --namespace external-secrets \
    --create-namespace
```

## Deploy secret store
```
kubectl apply -f secretstore.yaml
```
This creates a 'client' that is able to authenticate with the Key Vault to retrieve secrets

## Deploy external secrets
```
kubectl apply -f eternalsecret.yaml
```
Specify the secrets / keys / certificates to be imported from the Key Vault

## Verify secrets existance
```
kubectl describe secret external-secrets-demo --namespace external-secrets
```