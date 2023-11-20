# xinference-docker-hf

This project allows easy deployment of any built-in LLM of
[Xinference](https://github.com/xorbitsai/inference) using Docker. Uses Docker
and Docker compose, available [here](https://docs.docker.com/get-docker/).

## Installation and usage

The pre-built image is available on Docker Hub under the name
`biocypher/xinference-builtin` as a multi-arch image. You can pull it using
`docker pull biocypher/xinference-builtin`. The image is built for amd64 and
arm64 architectures. If you want to build the image yourself, you can use the
Dockerfile in this repository (step 2).

1. Install nvidia-docker libraries (find details about the Nvidia-Container
Toolkit [here](https://hub.docker.com/r/nvidia/cuda)).

2. Run `docker compose pull` to use a pre-built image or `docker compose build`
to build it locally.

3. Run `docker compose up -d`. This should start a container in the background
that downloads and runs the zephyr-7b model. To change the model, change the
env_file parameter in the `docker-compose.yml` file, for instance to
`llama-2-13b.env`.

4. Optional: There are two example environment file examples that can be
commented and un-commented in the docker-compose.yml. The llama-2-chat file
shows you how to use models that require a huggingface access token (if the
token is placed in the .env file).

## Info

You can find a list of available LLM models in two ways:

1. Set the environment variable `LIST=1` in the active .env file. Run
`docker-compose up`, which will run the container attached until it prints a
list of all available LLMs

2. Find a maybe not up-to-date list in the xinference documentation
[here](https://inference.readthedocs.io/en/latest/models/builtin/index.html)
