#!/bin/bash

# Update Ubuntu
sudo apt-get update

# Install dependencies
sudo apt-get -y install apt-transport-https ca-certificates

# Add the new GPG Key
apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E$

# Add Docker repository
sudo echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main" > /etc/ap$

# Update the system to load the new repo
sudo apt-get -y update

# Uninstall previous dockers installations
sudo apt-get -y purge lxc-docker

# Install necessary kernel-extras
sudo apt-get -y install linux-image-extra-$(uname -r) linux-image-extra-virtual

# Install Docker and start it
sudo apt-get -y install docker-engine
sudo service docker start

# Test the installation
sudo docker run hello-world | grep "Hello from Docker!" >> /dev/null

if [ $? -ne 0 ] ; then
    echo "Error occurred in Docker install"
fi

# Add Docker group for actual user
sudo groupadd docker
sudo usermod -aG docker $USER

# Start Docker on boot
sudo systemctl enable docker

