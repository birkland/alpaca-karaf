FROM karaf-test/karaf-base

RUN bin/start && \
    bin/client -r 10 -d 5  "feature:install fcrepo-indexing-triplestore" && \
    bin/client -r 10 -d 5  "feature:install islandora-indexing-triplestore" && \
    bin/stop && \
    rm -rf instances/*

COPY cfg/* etc/