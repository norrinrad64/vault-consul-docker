# Cluster vault consul avec docker-compose
* 3 containers consul ( Cluster pour le backend ) et 1 container vault

## Clone du repo
```
git clone https://github.com/norrinrad64/vault-consul-docker.git
```

### Vault : Changement du port dans docker-compose.yml
```
vault:
    build:
      context: ./vault
      dockerfile: Dockerfile
    ports:
      - 8080:8200
```

## Application vault exposée sur le port 8080 : `http://<IP>:8080`

## Consul : Changement du port dans docker-compose.yml
```
consul:
    build:
      context: ./consul
      dockerfile: Dockerfile
    ports:
      - 8081:8500
```
### Application consul exposée sur le port 8081 : `http://<IP>:8081/ui`

### Déploiement
```
cd vault-consul-docker
docker-compose up -d --build
docker-compose logs -f
```
## Init
```
docker-compose exec vault bash
vault operator init
vault operator unseal = A lancer 3 fois avec 3 Unseal Key différents
vault login s.xxxxxxxxxxxxxxxxxxxxxx
vault audit enable file file_path=/vault/logs/audit.log
```

## Nouvelle connexion
```
docker-compose exec vault bash
vault login <TOKEN>
```
