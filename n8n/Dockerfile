FROM node:20-alpine

LABEL org.opencontainers.image.authors="fc5570@danbor.host"

RUN npm install -g n8n && \
    apk add --no-cache bash dos2unix

RUN adduser -D -h /home/container container && \
    chown -R container:container /home/container
    
COPY --chown=container:container ./entrypoint.sh /entrypoint.sh
RUN dos2unix /entrypoint.sh && chmod +x /entrypoint.sh

USER container
ENV USER=container HOME=/home/container
ENV SHELL=/bin/sh
WORKDIR /home/container
    
EXPOSE 5678

CMD ["/bin/sh", "/entrypoint.sh"]