# :wheel_of_dharma: Graph Theory Course's PySpark Workspace

## :whale: Docker installation and usage

### Requirements

- [Docker](https://docs.docker.com/get-docker/)
- [Docker-compose](https://docs.docker.com/compose/install/)

### Building and running

First, make sure you are inside this repository's directory:

```bash
cd <path/to/repo>
```

Then, start the container:

```bash
docker-compose up --detach # starts the container in the background of your terminal
```

At this point, the Jupyter Notebook will be running at `http://localhost:8888`.

### Installing new packages

There are a few ways you may install new packages to the container. It'll depend on your goal and needs.

#### Pip

If you need to do update or add packages via `pip`, execute the following command **inside your jupyter notebook**:

```bash
import sys
!{sys.executable} -m pip install <package> # installs a pip package in the current Jupyter kernel
```

> _**note**_: the `!` notation is used to run `pip` directly as a shell command from the notebook. Also, take a look [here](https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter/) to see why you should NOT use `!pip install <package>`.

#### Conda

If you need to do update or add packages via `conda`, execute the following command **inside your jupyter notebook**:

```bash
import sys
!conda install --yes --prefix {sys.prefix} <package> # installs a conda package in the current Jupyter kernel
```

> _**note**_: the `!` notation is used to run `conda` directly as a shell command from the notebook. Also, take a look [here](https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter/) to see why you should NOT use `!conda install --yes <package>`.

#### System

To add or update system packages, you will need `root` user permissions. To achieve this, use the following command:

```bash
docker exec -it --user root tensorflow_notebook /bin/bash # executes the container's shell
sudo apt install <package>
# or `sudo apt update && sudo apt upgrade`                # updates installed packages
```

### Wrapping up

Once you're done, you may remove what was created by `up` with the following command:

```bash
docker-compose down # stops containers and removes containers, networks, volumes, and images created by `up`
```