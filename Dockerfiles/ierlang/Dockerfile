FROM matsubara0507/nine-lang-docker:latest

RUN pip install ipython jupyter

## ierlang

RUN git clone --depth 1 https://github.com/matsubara0507/simple-ierlang.git /root/ierlang
WORKDIR /root/ierlang
RUN cd kernels && jupyter kernelspec install erlang
