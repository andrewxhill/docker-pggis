AXH notes
=========

If you are using the latest docker tools on Mac, this ticket is probably helpful, http://stackoverflow.com/questions/32834082/how-to-increase-docker-machine-memory-mac

building
--------

build using

    docker build -t psql95 .
    docker build --no-cache -t psql95 .

to rebuild, run

    docker build -rm .

running
-------

normal run

    docker run -d -p localhost:5432:5432 --name db psql95 /sbin/my_init

double-check the port is available

    docker port db 5432

view the logs

    docker logs -f db

Docker notes
============

Using a docker repository
-------------------------

Login to docker.io servers and push a named image to the server.

```sh
sudo docker.io login
sudo docker.io push oslandia/pggis
```

Get the image from docker.io :

```sh
sudo docker.io pull oslandia/pggis
```

Using a Trusted Build
---------------------

In order to automate things better and save download/upload time, it is better to setup Trusted builds on docker.io

The docker_io branch from this repository is a Trusted Build on docker.io.
Each commit to the docker_io branch will automatically trigger a build on docker.io and make a new version of the oslandia/pggis image.

See more information on docker.io Trusted Build here : http://docs.docker.io/docker-io/builds/
