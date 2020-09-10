FROM     python:alpine

ARG      DOCKER_UID

# Create a user to run the application
RUN      adduser -D -u ${DOCKER_UID} flexget
WORKDIR  /home/flexget

# Data and config volumes
VOLUME   /home/flexget/.flexget
VOLUME   /home/flexget/torrents

# Install build dependencies and FlexGet
RUN      apk add --no-cache --virtual  .build-deps gcc musl-dev && \
         pip3 install -U pip && pip3 install flexget && \
         apk del .build-deps gcc musl-dev

# Add start script
COPY     start.sh /home/flexget/
RUN      chmod +x ./start.sh

USER     flexget
CMD      ["./start.sh"]
