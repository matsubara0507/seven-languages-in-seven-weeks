FROM matsubara0507/jupyter-six-lang:latest

## ihaskell

RUN apt-get update && apt-get install -y --no-install-recommends \
    libatlas-dev \
    libblas-dev \
    libcairo2-dev \
    liblapack-dev \
    libmagic-dev \
    libpango1.0-dev \
    libtinfo-dev \
    libzmq3-dev \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

RUN git clone --depth 1 https://github.com/abarbu/IHaskell.git /root/IHaskell
WORKDIR /root/IHaskell
RUN stack install gtk2hs-buildtools
RUN stack install --fast
RUN stack exec ihaskell -- install
