FROM matsubara0507/nine-lang-docker:latest

RUN pip install ipython jupyter

RUN git clone --depth 1 https://github.com/alexarchambault/jupyter-scala.git /root/iscala
WORKDIR /root/iscala
RUN curl -L -o coursier https://git.io/vgvpD \
 && chmod +x coursier \
 && mv coursier /usr/local/bin/
ADD jupyter-scala /root/iscala
RUN chmod +x jupyter-scala \
 && ./jupyter-scala
