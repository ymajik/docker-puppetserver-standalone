# Docker puppetserver standalone

[![Docker Automated build](https://img.shields.io/docker/automated/jrottenberg/ffmpeg.svg)](https://hub.docker.com/r/ymajik/puppetserver-standalone/builds/)
[![Build Status](https://travis-ci.org/ymajik/docker-puppetserver-standalone.svg?branch=testing)](https://travis-ci.org/ymajik/docker-puppetserver-standalone)

Docker image to run a standalone puppetserver, based on the https://github.com/puppetlabs/puppet-in-docker project,
with a fix for the timezone in Ubuntu 16.04

## Time / date
In the Ubuntu 16.04 image there is bug. Solution was

```bash
ENV TZ 'Europe/Tallinn'
RUN echo $TZ > /etc/timezone && \
	    apt-get update && apt-get install -y tzdata && \
	    rm /etc/localtime && \
	    ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && \
	    dpkg-reconfigure -f noninteractive tzdata && \
	    apt-get clean

```
