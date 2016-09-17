FROM osmtw/ubuntu

MAINTAINER Rex Tsai "https://about.me/chihchun"

ENV OSMOSIS_VERSION=0.44.1-4
ENV MAPSFORGE_VERSION=0.6.0

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
 && apt-get dist-upgrade -y

RUN apt-get install -y osmosis=${OSMOSIS_VERSION} wget

# Install Osmosis Mapsforge Map Writer
RUN wget http://ci.mapsforge.org/job/$MAPSFORGE_VERSION/lastSuccessfulBuild/artifact/mapsforge-map-writer/build/libs/mapsforge-map-writer-$MAPSFORGE_VERSION.jar \
 && mv mapsforge-map-writer-$MAPSFORGE_VERSION.jar /usr/share/osmosis

# https://github.com/mapsforge/mapsforge/issues/303
RUN echo  "load /usr/share/java/xalan2.jar"  >> /etc/osmosis/plexus.conf \
 && echo "JAVACMD_OPTIONS=-Xmx2G" > /root/.osmosis


RUN apt-get clean \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /data
