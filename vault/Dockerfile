# Image de base
FROM alpine:latest

# Version de vault https://releases.hashicorp.com/vault
ENV VAULT_VERSION 1.4.1

# Dossier vault
RUN mkdir /vault

# Packages
RUN apk --no-cache add bash ca-certificates  wget

# Download vault et installation
RUN wget --quiet --output-document=/tmp/vault.zip https://releases.hashicorp.com/vault/${VAULT_VERSION}/vault_${VAULT_VERSION}_linux_amd64.zip && \
    unzip /tmp/vault.zip -d /vault && \
    rm -f /tmp/vault.zip && \
    chmod +x /vault

# Ajout du PATH
ENV PATH="PATH=$PATH:$PWD/vault"

# Fichier de configuration vault
COPY ./config/vault-config.json /vault/config/vault-config.json

# Exposition du port 8200
EXPOSE 8200

# Démarrage de vault
ENTRYPOINT ["vault"]

