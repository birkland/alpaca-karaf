FROM openjdk:8-jre


# Karaf environment variables
ENV KARAF_VERSION=4.0.9 \
    ALPACA_VERSION=1.0.2 \
    ACTIVEMQ_VERSION=5.15.0 \
    CAMEL_VERSION=2.20.4
ENV APPS /opt
ENV KARAF_HOME $APPS/apache-karaf-${KARAF_VERSION}
ENV PATH $PATH:$KARAF_HOME/bin
WORKDIR $KARAF_HOME

# Download Karaf and make sure it logs to the console
RUN apt-get update && apt-get -y install procps && \
    curl -L http://archive.apache.org/dist/karaf/${KARAF_VERSION}/apache-karaf-${KARAF_VERSION}.tar.gz | tar xzf - -C ${APPS} && \
    sed -i 's@http://repo1@https://repo1@' ${KARAF_HOME}/etc/org.ops4j.pax.url.mvn.cfg && \
    sed -i 's/osgi:/stdout, osgi:/' ${KARAF_HOME}/etc/org.ops4j.pax.logging.cfg && \
    rm -rf /var/lib/apt/lists/* 

# Install common features and repos
RUN bin/start && \
    bin/client -r 10 -d 5  "feature:repo-add mvn:ca.islandora.alpaca/islandora-karaf/${ALPACA_VERSION}/xml/features" && \
    bin/client -r 10 -d 5  "feature:repo-add mvn:org.apache.activemq/activemq-karaf/${ACTIVEMQ_VERSION}/xml/features" && \
    bin/client -r 10 -d 5  "feature:repo-add mvn:org.apache.camel.karaf/apache-camel/${CAMEL_VERSION}/xml/features" && \
    bin/client -r 10 -d 5  "feature:install fcrepo-service-activemq" && \
    bin/client -r 10 -d 5  "feature:install fcrepo-service-camel" && \
    bin/client -r 10 -d 5  "feature:install islandora-http-client" && \
    bin/stop && \
    rm -rf instances/*

COPY cfg/* etc/

EXPOSE 8101 1099 44444 8181
CMD ["karaf", "server"]
