# Experiments with Alpaca (Karaf connectors)

Deploys Karaf connectors as separate Karaf instances, communicating with a single ActiveMQ instance.  There are no microervices in this experiment, just connectors and ActiveMQ.

## Quickstart

First, build the Karaf base image

    docker-compose.exe -f  karaf-base/docker-compose.yml build

Next, build all the rest of the images

    docker-compose build

Now, run

    docker-compose up -d

Hop into a running image to inspect via `docker exec`

Take a look at the environment variables in `.env`



 
