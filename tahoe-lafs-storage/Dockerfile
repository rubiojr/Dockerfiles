FROM ubuntu

MAINTAINER Sergio Rubio <rubiojr@frameos.org>

RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y python-pip build-essential python-dev less vim-tiny net-tools sed
RUN pip install twisted && pip install allmydata-tahoe

RUN adduser --gecos Tahoe --disabled-login tahoe
RUN mkdir -p /home/tahoe/node

ADD tahoe-bootstrap /usr/local/bin/tahoe-bootstrap
RUN chmod +x /usr/local/bin/tahoe-bootstrap
ADD tahoe.cfg /etc/tahoe.cfg.tmpl

ENTRYPOINT /usr/local/bin/tahoe-bootstrap
