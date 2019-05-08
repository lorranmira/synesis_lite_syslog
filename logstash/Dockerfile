# https://github.com/elastic/logstash-docker
FROM docker.elastic.co/logstash/logstash-oss:6.7.0

ENV SYNLITE_SYSLOG_ES_HOSTS="http://127.0.0.1:9200"
# Use port 1514 WITHIN container only due to JAVA priv ports problems
ENV SYNLITE_SYSLOG_TCP_PORT="1514"
ENV SYNLITE_SYSLOG_UDP_PORT="1514"
ENV SYNLITE_SYSLOG_SYSLOG_TZ="UTC"

#RUN $HOME/bin/logstash-plugin update logstash-input-udp \
#    && $HOME/bin/logstash-plugin update logstash-input-tcp \
#    && $HOME/bin/logstash-plugin update logstash-input-syslog \
#    && $HOME/bin/logstash-plugin update logstash-filter-dns

WORKDIR /usr/share/logstash/config
COPY --chown=logstash:logstash ./docker_assets/logstash.yml ./
COPY --chown=logstash:logstash ./docker_assets/pipelines.yml ./

WORKDIR /etc/logstash/synesis_lite_syslog
COPY --chown=logstash:root ./synesis_lite_syslog/ ./

ENTRYPOINT ["/usr/local/bin/docker-entrypoint"]

