FROM matsubara0507/nine-lang-docker:latest

RUN pip install ipython jupyter

## iruby

ENV RUBY_VERSION 2.4.1

WORKDIR /root
RUN /bin/bash -c "\
  source .bashrc \
 && rbenv install $RUBY_VERSION \
 && rbenv global $RUBY_VERSION \
 "\
 && echo 'eval "$(rbenv init -)"' >> .bashrc

RUN set -x && apt-get update && apt-get install -y --no-install-recommends \
    autoconf \
    automake \
    libffi-dev \
    libtool \
    libzmq-dev \
    pkg-config \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*
RUN git clone --depth=1 https://github.com/zeromq/czmq /root/czmq \
 && cd /root/czmq \
 && ./autogen.sh && ./configure && make && make install
RUN /bin/bash -c "\
    source .bashrc \
 && gem install cztop iruby \
 && iruby register --force \
 "
