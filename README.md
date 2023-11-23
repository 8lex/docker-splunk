# Docker-Splunk: Containerizing Splunk Enterprise with uid & guid=1000 and macs

![Docker Image Version (tag latest semver)](https://img.shields.io/docker/v/kruj0/splunk/latest?color=green&label=Splunk-UID:1000&style=for-the-badge)

![Docker Image Version (tag latest semver)](https://img.shields.io/docker/v/kruj0/splunk501/latest?color=green&label=Splunk-UID:Macs&style=for-the-badge)


A fork from splunk/docker-splunk with automated dockerhub images

----

# why?
I wanted to test&develop on my dev maschine and use my local IDE (VSC). Its not possible with the original images from splunk  because of hardcorded ARGS of UID & GID.

---
# mac supported
Since my dev machine is  a mac, i made also containers for my arm mac (rosetta emulation).
## Use Orbstack
Docker desktop is not recommented to use in the combination with a mac & this container. There are some issues with the filesystem drivers **virtioFS**. Which is not the case in orbstack!

---

# Big Changes between splunk original and this repo:

inside this repo its changed to for linux/ WSL you have 2 splunk images. 
Splunk which reflect this:
```
ARG UID=1000
ARG GID=1000
```

splunk501 which reflect this for mac dev machines:
```
ARG UID=501
ARG GID=20
```

## baseimage changes:

The baseimage is also modified with following entries to work inside the containers:
```
echo 'alias ll="ls --color -al"' >> /etc/bashrc
echo 'alias cs="clear;ls -lsh"' >> /etc/bashrc
echo 'alias ..="cd .."' >> /etc/bashrc
echo 'alias ...="cd ../.."' >> /etc/bashrc
echo 'alias splunk=/opt/splunk/bin/splunk' >> /etc/bashrc
``````

Two Github Actions are there to automate the build process to have finished docker images on dockerhub.

# Links

 [Dockerhub splunk](https://hub.docker.com/r/kruj0/splunk)

 [Dockerhub splunk501](https://hub.docker.com/r/kruj0/splunk501)
