# Création cluster 
* 3 containers consul et 1 container vault

## Application vault exposée sur le port 80
`http://0.0.0.0`

## Application consul exposée sur le port 8080
`http://0.0.0.0:8080/ui`

# Init

`docker-compose exec vault bash`
`vault operator init`
`vault operator unseal`
