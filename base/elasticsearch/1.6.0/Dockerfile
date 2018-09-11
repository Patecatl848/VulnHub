FROM openjdk:8-jre

LABEL maintainer="phithon <root@leavesongs.com>"

ADD logging.yml ./config/logging.yml
ADD docker-entrypoint.sh /

RUN set -ex \
    && mkdir -p /usr/share/elasticsearch \
    && wget -qO- https://download.elastic.co/elasticsearch/elasticsearch/elasticsearch-1.6.0.tar.gz | tar zx \
        --strip-components 1 -C /usr/share/elasticsearch \
    && chmod +x /docker-entrypoint.sh

ENV PATH /usr/share/elasticsearch/bin:$PATH
WORKDIR /usr/share/elasticsearch
EXPOSE 9200 9300

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["elasticsearch"]