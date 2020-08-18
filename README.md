{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Jupterhub deployed via docker containers including pyiron package\n",
    "This repository is forked from <a href=\"https://github.com/jupyterhub/jupyterhub-deploy-docker\">here</a>."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**The objective here is to create a dockerized jupyterhub which can spawn jupyter notebooks (with pyiron installed) as docker containers.**"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The structure of the repository is similar to <a href=\"https://github.com/jupyterhub/jupyterhub-deploy-docker\">the original repository</a>. Therefore, for more details you can refer to the repository. Here, I try to explain what modifications have been made."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Creating the image of a single-user notebook \n",
    "To build the single-user notebook images, first we use `make notebook`. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "In the `single-user/Dockerfile` file, we included installation of pyiron via conda-forge channel."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Building the docker-compose.yml\n",
    "In the second step, the hub image and the database image is created. By performing `make build`, beside creating docker volumes and copying several files (secrets, userlist, jupyterhub_config.py) to the created image, the `docker-compose.yml` file is used to create the image for the hub and the database."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The `jupyterhub_config.py` file sets the authentication class to PAM authenticator from the host machine. Additionally one needs to mount /etc/passwd and /etc/shadow on to the image. This is implemented in the `docker-compose.yml` file."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "There are minor changes to the `Dockerfile.jupyterhub` file to include conda package in the docker image."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.6"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
