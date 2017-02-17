# Dockerfile to build NEST

http://www.nest-simulator.org/

Based on Ubuntu

* Python3
* Jupyter

## Build

docker build -t nest .

## Run

docker run -it -p 8888:8888 nest /bin/bash

jupyter notebook --ip 0.0.0.0 --no-browser
