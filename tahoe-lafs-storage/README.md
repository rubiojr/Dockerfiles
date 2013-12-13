# Tahoe-LAFS Storage Node

Edit tahoe.cfg to set `nickname` and `introducer.furl` and build the image. Then:

    sudo docker build -rm -t tahoe-storage
    
Script to run the storage node:

    # Change it to the path where the data will be stored
    STORAGE_PATH=/data/node1
    # Do not change the container mount point (/home/tahoe/storage)
    # Redirects local port 58272 to the container port 58272
    # See http://docs.docker.io/en/latest/use/port_redirection/#port-redirection
    sudo docker run -p 58272:58272 \
                    -name my-node \
                    -v $STORAGE_PATH:/home/tahoe/storage:rw \
                    -i -t tahoe-storage
