We are using `GitHub Container Registry`. So we need to create a secret to authenticate to `GHCR`.

```bash
kubectl create secret docker-registry ghcr-secret --docker-server=ghcr.io --docker-username=<GH_USERNAME> --docker-password=<GH_ACCESS_TOKEN> --docker-email=<EMAIL>
```
We need to create secrets for anokha-frontend.

Copy the `anokha-frontend-secret.yml` file. <br>
Add the base 64 encoded values of 
- is-production,
- payu-key-test,
- payu-key-prod.

> [!TIP]  
> Use this linux command to encode data in base64 format. <br>
> ```bash
>  echo —n <VALUE_TO_ENCODE> | base64
> ```

Run
```bash
kubectl apply -f anokha-frontend-secret.yaml
``` 
Now the secret will be created.

Then copy the `anokha-frontend.yaml` file and run

```bash
kubectl apply -f anokha-frontend.yaml
``` 
This creates the pods and required services to run the application.
