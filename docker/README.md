Since we are using raspberry pis for kubernetes deployment, we must ensure we are using `arm` compatible docker images.
Buildx helps us build `multi-arch` images on docker.

To see which builder we are using to build images.

```bash
docker buildx ls
```

