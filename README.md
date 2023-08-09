# Pytorch Development Docker Image

Based off of the [official pytorch image](https://hub.docker.com/r/pytorch/pytorch/) but with some additional development tools installed.

## Usage

Use as a base image in your `Dockerfile`:

```
FROM ghcr.io/chadly/pytorch:latest

RUN git clone https://github.com/m-bain/whisperX.git /app

WORKDIR /app
RUN pip install -e .

CMD whisperx --help
```

or directly with `docker compose`:

```
services:
  cli:
    image: ghcr.io/chadly/pytorch:latest
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
