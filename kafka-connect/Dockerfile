FROM confluentinc/cp-kafka-connect-base:5.3.0

COPY mongodb-kafka-connect.tar.gz .

RUN mkdir plugins-connector \
    && tar xzf mongodb-kafka-connect.tar.gz -C plugins-connector

ENV CONNECT_PLUGIN_PATH="/usr/share/java,/plugins-connector"

WORKDIR /usr/app

COPY connect/ .
RUN chmod +x *.sh

CMD [ "/bin/bash", "-c", "echo \"Launching Kafka Connect worker\" & \
        /etc/confluent/docker/run & /usr/app/start-and-wait.sh"]
