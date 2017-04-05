FROM openjdk:8

ENV HOME /root
WORKDIR $HOME

# Prolog

RUN apt-get update && apt-get install -y --no-install-recommends \
    gprolog \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
