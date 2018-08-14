FROM nvidia/cuda:9.0-cudnn7-devel-ubuntu16.04

# Update system.
RUN apt-get -y update && \
    apt-get -y upgrade

# Install Python3
RUN apt-get install -y python3.5 python3-pip python-virtualenv