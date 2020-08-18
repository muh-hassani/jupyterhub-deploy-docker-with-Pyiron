## Jupterhub deployed via docker containers including pyiron package
This repository is forked from <a href="https://github.com/jupyterhub/jupyterhub-deploy-docker">here</a>.

**The objective here is to create a dockerized jupyterhub which can spawn jupyter notebooks (with pyiron installed) as docker containers.**

The structure of the repository is similar to <a href="https://github.com/jupyterhub/jupyterhub-deploy-docker">the original repository</a>. Therefore, for more details you can refer to the repository. Here, I try to explain what modifications have been made.

### Creating the image of a single-user notebook 
To build the single-user notebook images, first we use `make notebook`. 

In the `single-user/Dockerfile` file, we included installation of pyiron via conda-forge channel.

## Building the docker-compose.yml
In the second step, the hub image and the database image is created. By performing `make build`, beside creating docker volumes and copying several files (secrets, userlist, jupyterhub_config.py) to the created image, the `docker-compose.yml` file is used to create the image for the hub and the database.

The `jupyterhub_config.py` file sets the authentication class to PAM authentication from the host machine. Additionally one needs to mount /etc/pass and /etc/shadows on to the image. This is implemented in the `docker-compose.yml` file.

There are minor changes to the `Dockerfile.jupyterhub` file to include conda package in the docker image.
