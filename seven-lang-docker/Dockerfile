FROM openjdk:8

MAINTAINER MATSUBARA Nobutada

WORKDIR ~

# Ruby
## use rbenv

RUN apt-get update && apt-get install -y --no-install-recommends \
    g++ \
    gcc \
    make \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv
RUN cd ~/.rbenv \
    && src/configure \
    && make -C src
RUN git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
RUN echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc

# Io

RUN apt-get update && apt-get install -y --no-install-recommends \
    cmake \
    g++ \
    libyajl-dev \
    libpython3.4-dev \
    libgmp-dev \
    libmemcached-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN git clone --branch 2015.11.11 --depth 1 https://github.com/stevedekorte/io.git ~/io \
    && mkdir -p ~/io/build \
    && cd ~/io/build \
    && cmake .. \
    && make install \
    && rm -fr ~/io

ENV PATH /usr/local/bin:$PATH

# Prolog

RUN apt-get update && apt-get install -y --no-install-recommends \
    gprolog \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

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

# Erlang

RUN echo "deb http://packages.erlang-solutions.com/debian jessie contrib" >> /etc/apt/sources.list \
    && wget http://packages.erlang-solutions.com/ubuntu/erlang_solutions.asc \
    && apt-key add erlang_solutions.asc \
    && apt-get update && apt-get install -y --no-install-recommends \
    erlang \
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
## with Stack

RUN echo 'deb http://ppa.launchpad.net/hvr/ghc/ubuntu trusty main' > /etc/apt/sources.list.d/ghc.list \
    && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F6F88286 \
    && apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    g++ \
    ghc-8.0.2 \
    libtinfo-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 575159689BEFB442 \
    && echo 'deb http://download.fpcomplete.com/debian jessie main' | tee /etc/apt/sources.list.d/fpco.list \
    && apt-get update && apt-get install -y --no-install-recommends \
    stack \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN stack config set system-ghc --global true
ENV PATH /opt/ghc/8.0.2/bin:$PATH

# run /bin/bash by default unless a command is specified
CMD ["/bin/bash"]
