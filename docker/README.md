Since we are using raspberry pis for kubernetes deployment, we must ensure we are using `arm` compatible docker images.
Buildx helps us build `multi-arch` images on docker.

I referred to this [blog](https://nickjanetakis.com/blog//build-multi-cpu-architecture-docker-images-with-buildx) to configure and use Buildx.

To see which builder we are using to build images.

```bash
docker buildx ls
```

To create a multi-arch builder

```bash
docker buildx create --driver-opt network=host --use --name multi-arch
```
> [!NOTE]
> ### Optional
> Now builder will switch to multi-arch but, build instance will be inactive, the previous default instance will be active. We have to switch to multi-arch.
>
> ```bash
> docker buildx inspect multi-arch --bootstrap
> ```

Build multi-arch image
```bash
docker buildx build --platform linux/amd64,linux/arm64 -t <IMAGE_TAG> .
```
> [!WARNING]
> This only builds the image, it doesn't load it into the local device image store. 
> - To load, we shoud use `--load` during build
>     - But load flag cant load multiarch images to image store. So we need to specify one architecture.
> - To push to registry directly, we should use `--push`. (This supports multiarch directly)


