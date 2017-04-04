FROM openjdk:8

MAINTAINER MATSUBARA Nobutada

WORKDIR ~

# Erlang

RUN echo "deb http://packages.erlang-solutions.com/debian jessie contrib" >> /etc/apt/sources.list \
    && wget http://packages.erlang-solutions.com/ubuntu/erlang_solutions.asc \
    && apt-key add erlang_solutions.asc \
    && apt-get update && apt-get install -y --no-install-recommends \
    erlang \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
