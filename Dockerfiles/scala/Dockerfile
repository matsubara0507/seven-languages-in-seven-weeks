FROM openjdk:8

WORKDIR ${HOME}

# Scala
## with sbt

ENV SCALA_VERSION 2.12.1

RUN curl -fsL "http://downloads.typesafe.com/scala/$SCALA_VERSION/scala-$SCALA_VERSION.tgz" | tar xfz - -C ~ \
    && mv "$HOME/scala-$SCALA_VERSION" "$HOME/.scala" \
    && echo "export PATH=~/.scala/bin:$PATH" >> ~/.bashrc
RUN apt-get update && apt-get install -y --no-install-recommends \
    apt-transport-https \
    && echo "deb https://dl.bintray.com/sbt/debian/" | tee -a /etc/apt/sources.list.d/sbt.list \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823 \
    && apt-get update && apt-get install -y --no-install-recommends \
    sbt \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && sbt sbtVersion
