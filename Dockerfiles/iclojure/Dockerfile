FROM matsubara0507/nine-lang-docker:latest

RUN pip install ipython jupyter

## iclojure

RUN git clone --depth 1 https://github.com/roryk/clojupyter /root/clojupyter
WORKDIR /root/clojupyter
RUN make && make install
