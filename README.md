# XCI

- This repository contains the code and resources for developing a robust pipeline for analysing X-inactivation (XCI) using bulk and single-cell RNA sequencing. 


# To run

## Docker
```
# Build Docker image (general command)
docker build -t <NAME>:<TAG> -f <PATH_TO_DOCKERFILE>

# To run a Docker contianer interactively
docker run -it <NAME>:<TAG>

# To push a Docker image to DockerHub
docker push <NAME>:<TAG>
```

## Singularity
```
# Too pull a Docker image from DockerHub
singulairty pull docker://<NAME>:<TAG>

# To run a Docker contianer interactively
docker run -it <NAME>:<TAG>

# To run a SIF
singularity run <NAME>.sif
```

