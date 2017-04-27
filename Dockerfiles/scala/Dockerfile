FROM openjdk:8

ENV HOME /root
WORKDIR $HOME

# Scala
## with sbt

ENV SCALA_VERSION 2.12.1
ENV SBT_VERSION 0.13.15

RUN curl -fsL "http://downloads.typesafe.com/scala/$SCALA_VERSION/scala-$SCALA_VERSION.tgz" | tar xfz - -C ~ \
    && mv "$HOME/scala-$SCALA_VERSION" "$HOME/.scala"
RUN curl -fsL "http://downloads.typesafe.com/sbt/$SBT_VERSION/sbt-$SBT_VERSION.tgz" | tar xfz - -C ~ \
    && mv "$HOME/sbt" "$HOME/.sbt"
ENV PATH $HOME/.sbt/bin:$HOME/.scala/bin:$PATH
RUN sbt sbtVersion
