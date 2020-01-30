FROM karaf-test/karaf-base

RUN bin/start && \
    bin/client -r 10 -d 5  "feature:install islandora-indexing-fcrepo" && \
    bin/stop && \
    rm -rf instances/*

COPY ca.islandora.alpaca.indexing.fcrepo.cfg etc/