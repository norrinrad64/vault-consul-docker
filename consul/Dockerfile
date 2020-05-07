# Image de base
FROM alpine:latest

# Version de consul : https://releases.hashicorp.com/consul
ENV CONSUL_VERSION 1.7.3

# Dossier consul
RUN mkdir /consul

# Packages
RUN apk --no-cache add \
      bash \
      ca-certificates \
      wget

# Download consul et installation
RUN wget --quiet --output-document=/tmp/consul.zip https://releases.hashicorp.com/consul/${CONSUL_VERSION}/consul_${CONSUL_VERSION}_linux_amd64.zip && \
    unzip /tmp/consul.zip -d /consul && \
    rm -f /tmp/consul.zip && \
    chmod +x /consul/consul

# Ajout du PATH
ENV PATH="PATH=$PATH:$PWD/consul"

# Fichier de configuration consul
COPY ./config/consul-config.json /consul/config/config.json

# Exposition des ports 8300 8400 8500 8600
EXPOSE 8300 8400 8500 8600

# Démarrage de consul
ENTRYPOINT ["consul"]
