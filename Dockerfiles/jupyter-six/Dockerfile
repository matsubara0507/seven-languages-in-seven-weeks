FROM matsubara0507/nine-lang-docker:latest
RUN pip install ipython jupyter
# # iruby
ENV RUBY_VERSION="2.4.1"
WORKDIR /root
RUN /bin/bash -c " source .bashrc \
 && rbenv install $RUBY_VERSION \
 && rbenv global $RUBY_VERSION " \
 && echo 'eval "$(rbenv init -)"' >> .bashrc
RUN set -x \
 && apt-get update \
 && apt-get install -y --no-install-recommends autoconf automake libffi-dev libtool libzmq-dev pkg-config \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*
RUN git clone --depth=1 https://github.com/zeromq/czmq /root/czmq \
 && cd /root/czmq \
 && ./autogen.sh \
 && ./configure \
 && make \
 && make install
RUN /bin/bash -c " source .bashrc \
 && gem install cztop iruby \
 && iruby register --force "
# # iio
RUN git clone --depth 1 https://github.com/matsubara0507/iio.git /root/iio
WORKDIR /root/iio
RUN cd kernels \
 && jupyter kernelspec install io
# # iprolog
RUN git clone --depth 1 https://github.com/matsubara0507/iprolog.git /root/iprolog
WORKDIR /root/iprolog
RUN cd kernels \
 && jupyter kernelspec install prolog
RUN git clone --depth 1 https://github.com/alexarchambault/jupyter-scala.git /root/iscala
WORKDIR /root/iscala
RUN curl -L -o coursier https://git.io/vgvpD \
 && chmod +x coursier \
 && mv coursier /usr/local/bin/
ADD jupyter-scala /root/iscala
RUN chmod +x jupyter-scala \
 && ./jupyter-scala
# # ierlang
RUN git clone --depth 1 https://github.com/matsubara0507/simple-ierlang.git /root/ierlang
WORKDIR /root/ierlang
RUN cd kernels \
 && jupyter kernelspec install erlang
# # iclojure
RUN git clone --depth 1 https://github.com/roryk/clojupyter /root/clojupyter
WORKDIR /root/clojupyter
RUN make \
 && make install

