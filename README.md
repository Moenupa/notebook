# Jupyter Notebook

Jupyter Notebook workspace for the server (for personal uses).

This git repo is only for storing contents. To set up a similar project, follow the instructions below:

## Setup

1. Download Docker and any jupyter notebook templates. Visit [Docker: Jupyter](https://hub.docker.com/u/jupyter) for more details.
2. Run an instance as demonstrated below: (where `jupyter/tensorflow-notebook` replaced by name of your docker image)
  ```sh
  $ sudo docker run --name notebook -d -p 8888:8888 -v "${pwd}":/home/jovyan/work jupyter/tensorflow-notebook
  ```
  And output should be like
  ```sh
  $ sudo docker logs notebook 2>&1 | grep token | tail -n 2
          http://9a631037a22f:8888/lab?token=<yourtokenhere>
       or http://127.0.0.1:8888/lab?token=<yourtokenhere>
  ```

Your site is ready

## Optimize

1. with some extensions to improve its functionality
  ```sh
  $ sudo docker exec -it notebook /bin/bash
  (base) jovyan@9a631037a22f $ conda install -c conda-forge jupyter_contrib_nbextensions -q -y
  (base) jovyan@9a631037a22f $ jupyter contrib nbextension install --user
  (base) jovyan@9a631037a22f $ conda install -c conda-forge jupyter_nbextensions_configurator -q -y
  (base) jovyan@9a631037a22f $ jupyter nbextensions_configurator enable --user
  ```
2. with custom theme for better readability
  ```
  $ conda install -c conda-forge jupyterthemes
  $ jt -t monokai -T -N -kl
  ```
 
