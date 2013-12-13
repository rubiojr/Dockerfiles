# sudo docker run -v /home/rubiojr/tmp:/home/tahoe/storage:rw tahoe-storage-node
FROM ubuntu

MAINTAINER Sergio Rubio <rubiojr@frameos.org>

RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y python-pip build-essential python-dev less vim-tiny net-tools 
RUN pip install twisted && pip install allmydata-tahoe

RUN adduser --gecos Tahoe --disabled-login tahoe
RUN find /home/tahoe/ -type f -exec rm -f {} \;

RUN su -c 'tahoe create-node -p none /home/tahoe/' tahoe

ADD client.port /home/tahoe/client.port
#RUN tahoe create-node -p none /home/tahoe/
RUN chown tahoe:tahoe -R /home/tahoe

ENTRYPOINT /usr/local/bin/tahoe start /home/tahoe && cat
USER tahoe

# Expose tahoe storage node port
# We can also do this when running the container via -expose
# EXPOSE 58272
