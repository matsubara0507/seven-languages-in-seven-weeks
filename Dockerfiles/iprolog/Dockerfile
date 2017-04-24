FROM matsubara0507/nine-lang-docker:latest

RUN pip install ipython jupyter

## iprolog

RUN git clone --depth 1 https://github.com/matsubara0507/iprolog.git /root/iprolog
WORKDIR /root/iprolog
RUN cd kernels && jupyter kernelspec install prolog
