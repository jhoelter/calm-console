FROM kibana:4.5.1

RUN apt-get update
RUN apt-get -y install curl

COPY kibana.yml /opt/kibana/config/kibana.yml
COPY jhipster-console.svg /tmp/jhipster-console.svg
COPY dashboards /tmp/dashboards/
COPY load.sh /tmp/load.sh
RUN chmod +x /tmp/load.sh
RUN sed -i -e 's/\r$//' /tmp/load.sh

RUN kibana plugin --install elastic/timelion


COPY ./entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
RUN sed -i -e 's/\r$//' /entrypoint.sh

VOLUME ["/tmp/dashboards"]

CMD ["/entrypoint.sh"]
