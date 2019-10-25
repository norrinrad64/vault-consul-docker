# Cluster vault consul

* 3 containers consul et 1 container vault

### Application vault exposée sur le port 80
* `http://0.0.0.0`

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
* `http://0.0.0.0:8080/ui`
## Changement du port dans docker-compose.yml
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
vault operator unseal
```
