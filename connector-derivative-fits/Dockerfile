FROM karaf-test/karaf-base

RUN bin/start && \
    bin/client -r 10 -d 5  "feature:install islandora-connector-derivative" && \
    bin/stop && \
    rm -rf instances/*

COPY ca.islandora.alpaca.connector.fits.blueprint.xml deploy/
COPY ca.islandora.alpaca.connector.fits.cfg etc/