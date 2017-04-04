FROM openjdk:8

MAINTAINER MATSUBARA Nobutada

WORKDIR ~

# Clojure
## use Leiningen

RUN wget https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein \
    && mv lein /usr/local/bin \
    && chmod u+x /usr/local/bin/lein
ENV LEIN_ROOT 1
RUN lein
