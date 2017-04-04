FROM openjdk:8

WORKDIR ${HOME}

# Io

RUN apt-get update && apt-get install -y --no-install-recommends \
    cmake \
    g++ \
    gcc \
    libyajl-dev \
    libpython3.4-dev \
    libgmp-dev \
    libmemcached-dev \
    make \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN git clone --branch 2015.11.11 --depth 1 https://github.com/stevedekorte/io.git ~/io \
    && mkdir -p ~/io/build \
    && cd ~/io/build \
    && cmake .. \
    && make install \
    && rm -fr ~/io

ENV PATH /usr/local/bin:$PATH
