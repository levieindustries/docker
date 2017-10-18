FROM postgres:10.0-alpine

RUN apk --update add curl

ENV CONTAINERPILOT=/etc/containerpilot.json5
ENV CONTAINERPILOT_VERSION 3.5.0
RUN curl -Lso /tmp/containerpilot.tar.gz \
      "https://github.com/joyent/containerpilot/releases/download/${CONTAINERPILOT_VERSION}/containerpilot-${CONTAINERPILOT_VERSION}.tar.gz" \
    && tar -xz -f /tmp/containerpilot.tar.gz \
    && mv containerpilot /bin/ \
    && rm /tmp/containerpilot.tar.gz

COPY containerpilot.json /etc/

ENV CONSUL_URL consul

CMD ["containerpilot", "/docker-entrypoint.sh", "postgres"]
