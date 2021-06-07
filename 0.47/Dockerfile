FROM ubuntu:20.04

LABEL maintainer="Iosif Pravets \"github.com/pravets\""

ENV OSMOSIS_VERSION=0.45
ENV MAPSFORGE_VERSION=0.6.1

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y --no-install-recommends wget

# Install prebuilt Osmosis
RUN wget https://bretth.dev.openstreetmap.org/osmosis-build/osmosis-${OSMOSIS_VERSION}.tgz --no-check-certificate
RUN mkdir -p /usr/local/osmosis \
 && tar zxvf osmosis-${OSMOSIS_VERSION}.tgz -C /usr/local/osmosis
# Install Osmosis Mapsforge Map Writer

RUN wget https://repo1.maven.org/maven2/org/mapsforge/mapsforge-map-writer/$MAPSFORGE_VERSION/mapsforge-map-writer-$MAPSFORGE_VERSION-jar-with-dependencies.jar --no-check-certificate \
 && mv mapsforge-map-writer-$MAPSFORGE_VERSION-jar-with-dependencies.jar /usr/local/osmosis


# https://github.com/mapsforge/mapsforge/issues/303
RUN echo  "load /usr/share/java/xalan2.jar"  >> /usr/local/osmosis/config/plexus.conf \
 && echo "JAVACMD_OPTIONS=-Xmx2G" > /root/.osmosis

RUN ln -s /usr/local/osmosis/bin/* /usr/bin
RUN apt-get install -y --no-install-recommends default-jre-headless  \
    libbatik-java \
    libcommons-codec-java \
    libcommons-compress-java \
    libcommons-dbcp-java \
    libcommons-pool-java \
    libjpf-java \
    #libmysql-java \
    #libnetty-3.9-java \
    libpostgis-java \
    libpostgresql-jdbc-java \ 
    libspring-beans-java \
    libspring-context-java \
    libspring-core-java \
    libspring-jdbc-java \
    libspring-transaction-java \
    libosmpbf-java \
    libplexus-classworlds-java \
    libprotobuf-java \
    libxerces2-java \
    libxz-java


RUN apt-get clean \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /data
