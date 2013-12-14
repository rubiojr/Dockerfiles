# Tahoe-LAFS Storage Node

Edit tahoe.cfg to set `nickname` and `introducer.furl` and build the image. Then:

    sudo docker build -rm -t tahoe-storage
    
Script to run the storage node:

    # Change it to the path where the tahoe node data and the config
    # will be stored.
    STORAGE_PATH=/data/node1
    # Do not change the container mount point (/home/tahoe/storage)
    # Redirects local port 58272 to the container port 58272
    # See http://docs.docker.io/en/latest/use/port_redirection/#port-redirection
    sudo docker run -e TAHOE_PORT=12346 -e TAHOE_INTRODUCER_FURL=bar -e TAHOE_NICKNAME=nick -name foo -v /home/rubiojr/tmp/foo:/home/tahoe/node:rw -i -t -tahoe-storage-node
    sudo docker run -e TAHOE_PORT=12346 \
                    -e TAHOE_NICKNAME=server01 \
                    -e TAHOE_INTRODUCER_FURL=pb://bleh \
                    -p 58272:12346 \
                    -name my-node \
                    -v $STORAGE_PATH:/home/tahoe/node:rw \
                    -i -t tahoe-storage
