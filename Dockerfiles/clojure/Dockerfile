FROM openjdk:8

ENV HOME /root
WORKDIR $HOME

# Clojure
## use Leiningen

RUN curl -O https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein \
    && mv lein /usr/local/bin \
    && chmod u+x /usr/local/bin/lein
ENV LEIN_ROOT 1
RUN lein
