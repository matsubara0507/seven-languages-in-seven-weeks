FROM openjdk:8

MAINTAINER MATSUBARA Nobutada

WORKDIR ~

# Scala
## with sbt

RUN apt-get update && apt-get install -y --no-install-recommends \
    scala \
    apt-transport-https \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823 \
    && apt-get update && apt-get install -y --no-install-recommends \
    sbt \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
