# Docker Alpaca Karaf connector

Produces a Karaf image with all Alpaca connectors running inside.

By default all connectors are 'inactive' (technically running, but not able to consume messages) unless configured via environment variables.  
See the `.env` file for a list of all environment variables supported by this connector. 


## Quickstart

First, build the Karaf base image

    docker-compose build

Then run with

    docker-compose up -d

Hop into a running image to inspect via `docker exec`

Take a look at the environment variables in `.env`

## Configuration

Require environment variables include:
* ACTIVEMQ_URL - ActiveMQ connection URI
* ACTIVEMQ_USERNAME - Username for connecting to ActiveMQ
* ACTIVEMQ_PASSWORD - Password for connecting to ActiveMQ.
* ALPACA_HTTP_TOKEN - Token for authenticating via JWT with secure Islandora services

See the `.env` file for a comprehensive list of envronment variables.  Comment Remove or comment out environment variables for a service you'd 
like to disable.

For example, by default Houdini is enabled, and configured as

```
ALPACA_HOUDINI_QUEUE=broker:queue:islandora-connector-houdini
ALPACA_HOUDINI_DERIVATIVE_SERVICE_URL=http://houdini:8000/convert
```

To disable the Houdini connector, simply comment out or remove these environment variables and re-start the Alpaca Karaf connector service.


 
