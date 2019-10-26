# Cluster vault consul avec docker-compose
* 3 containers consul et 1 container vault

## Clone du repo et docker-compose
```
git clone https://github.com/norrinrad64/vault-consul-docker.git
cd vault-consul-docker
docker-compose up -d --build
docker-compose logs -f
```

### Application vault exposée sur le port 80
* `http://<IP>:80`

### Changement du port dans docker-compose.yml
```
vault:
    build:
      context: ./vault
      dockerfile: Dockerfile
    ports:
      - 80:8200
```
### Application consul exposée sur le port 8080
* `http://<IP>:8080/ui`
### Changement du port dans docker-compose.yml
```
consul:
    build:
      context: ./consul
      dockerfile: Dockerfile
    ports:
      - 8080:8500
```
## Init
```
docker-compose exec vault bash
vault operator init
vault operator unseal = A lancer 3 fois avec 3 Unseal Key différents
vault audit enable file file_path=/vault/logs/audit.log
```

## Nouvelle connexion
```
docker-compose exec vault bash
vault login <TOKEN>
```
