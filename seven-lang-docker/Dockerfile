FROM debian:jessie

MAINTAINER MATSUBARA Nobutada

# Commom

WORKDIR ~
RUN apt-get update && apt-get install -y \
    cmake \
    g++ \
    gcc \
    git \
    make \
    wget \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN mkdir ~/git

## JVM

RUN apt-get update && apt-get install -y \
    software-properties-common \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN add-apt-repository "deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main" \
    && echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections
RUN apt-get update && apt-get install -y \
    oracle-java8-installer \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Ruby
## use rbenv

RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv
RUN cd ~/.rbenv \
    && src/configure \
    && make -C src
RUN git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build

ENV PATH $HOME/.rbenv/bin:$PATH

# Io

RUN apt-get update && apt-get install -y \
    libyajl-dev \
    libpython3.4-dev \
    libgmp-dev \
    libmemcached-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN git clone --branch 2015.11.11 --depth 1 https://github.com/stevedekorte/io.git ~/git/io
RUN mkdir -p ~/git/io/build \
    && cd ~/git/io/build \
    && cmake .. \
    && make install

ENV PATH /usr/local/bin:$PATH

# Prolog

RUN apt-get update && apt-get install -y \
    gprolog \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Scala
## with sbt

RUN apt-get update && apt-get install -y \
    scala \
    apt-transport-https \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823
RUN apt-get update && apt-get install -y \
    sbt \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Erlang

RUN echo "deb http://packages.erlang-solutions.com/debian jessie contrib" >> /etc/apt/sources.list \
    && wget http://packages.erlang-solutions.com/ubuntu/erlang_solutions.asc \
    && apt-key add erlang_solutions.asc
RUN apt-get update && apt-get install -y \
    erlang \
    erlang-base-hipe \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Clojure
## use Leiningen

RUN wget https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein \
    && mv lein /usr/local/bin \
    && chmod u+x /usr/local/bin/lein
ENV LEIN_ROOT 1
RUN lein

# Haskell
## use Stack

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 575159689BEFB442 \
    && echo 'deb http://download.fpcomplete.com/debian jessie main' | tee /etc/apt/sources.list.d/fpco.list
RUN apt-get update && apt-get install -y \
    stack \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN stack setup

# run /bin/bash by default unless a command is specified
CMD ["/bin/bash"] 
