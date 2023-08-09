# Pytorch Development Docker Image

Based off of the [official pytorch image](https://hub.docker.com/r/pytorch/pytorch/) but with some additional development tools installed.

## Usage

Use with `docker compose`:

```
services:
  cli:
    image: whisperx:latest
    container_name: myapp
    build:
      context: .
      dockerfile: Dockerfile

    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              device_ids: ['0']
              capabilities: [gpu]
```

or with `docker run`:

```
docker run --gpus all -it --rm whisperx:latest
```
