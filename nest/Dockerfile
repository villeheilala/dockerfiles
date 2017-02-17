############################################################
# Dockerfile to build NEST
# Based on Ubuntu
# Includes Python3, Jupyter, NEST
############################################################

# Set the base image to Ubuntu
FROM ubuntu:16.04

# File Author / Maintainer
MAINTAINER Ville Heilala

################## BEGIN INSTALLATION ######################

# Update the repository sources list and install
RUN apt-get update && apt-get install -yq \
	build-essential \
	cmake \
	cython \
	git \
	ipython \
	libgsl0-dev \
	libltdl7-dev \
	libncurses5-dev \
	libopenmpi-dev \
	libreadline6-dev \
	openmpi-bin \
	python \
	python3 \
	python3-all-dev \
	python3-matplotlib \
	python3-nose \
	python3-numpy \
	python3-pip \
	python3-scipy && \
	rm -rf /var/lib/apt/lists/*

RUN pip3 install --upgrade pip && \
	pip3 install jupyter

RUN git clone https://github.com/nest/nest-simulator.git && cd nest-simulator && \
	cmake \
		-DCMAKE_INSTALL_PREFIX=/usr/bin/nest \
#		-DPYTHON_EXECUTABLE=/usr/bin/python3 \
#		-DPYTHON_LIBRARY=/usr/lib/python3.5/config-3.5m-x86_64-linux-gnu/libpython3.5m.so \
#		-DPYTHON_INCLUDE_DIR=/usr/include/python3.5 \
#		-DPYTHON_INCLUDE_DIR2=/usr/include/x86_64-linux-gnu/python3.5m \
		-Dwith-python=3 \
        /nest-simulator && \
	make && make install && \
	echo 'source /usr/bin/nest/bin/nest_vars.sh' >> ~/.bashrc

##################### INSTALLATION END #####################
