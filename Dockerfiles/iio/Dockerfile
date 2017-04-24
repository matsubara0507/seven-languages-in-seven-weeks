FROM matsubara0507/nine-lang-docker:latest

RUN pip install ipython jupyter

## iio

RUN git clone --depth 1 https://github.com/matsubara0507/iio.git /root/iio
WORKDIR /root/iio
RUN cd kernels && jupyter kernelspec install io
