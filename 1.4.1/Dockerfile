FROM marceloagmelo/java:7

MAINTAINER Marcelo Melo <marceloagmelo@gmail.com>

ENV BASE=/opt
ENV SOLR_HOME=${BASE}/solr
ENV SOLR_USER solr
ENV SOLR_UID 8983

RUN groupadd -r -g $SOLR_UID $SOLR_USER && \
  useradd -r -u $SOLR_UID -g $SOLR_USER $SOLR_USER

RUN (mkdir -p ${SOLR_HOME})

# copy solr
COPY solr/ ${SOLR_HOME}/

ADD start.sh ${SOLR_HOME}/
RUN chmod 755 ${SOLR_HOME}/start.sh

RUN (sudo chown -R $SOLR_USER:$SOLR_USER ${SOLR_HOME})

USER $SOLR_USER

WORKDIR ${SOLR_HOME}/

VOLUME ["/opt/solr"]

ENV PATH /opt/solr:$PATH

EXPOSE 8983
CMD ["/opt/solr/start.sh", "run"]
