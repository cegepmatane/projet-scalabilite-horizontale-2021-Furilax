# Comment installer l'application et son environnement scalabilité horizontale ?

### Création mise en place des machines virtuelles

Dans un premier temps, il faut créer six machines virtuelles avec Docker Compose ainsi que des adresses IP allant de 192.168.56.10 à 192.168.56.15 et les nommées de façons claires (exemple : swarm-0 pour la première machine etc).

### Initialiser le cluster sur swarm-0 

<code>sudo docker swarm init --advertise-addr 192.168.56.10</code>

Le résultat de la commande renvoit un token **worker** qu'il faudra récupérer pour la suite.

<code>sudo docker swarm join-token manager</code>

Le résultat de la commande renvoit un token **manager** qu'il faudra récupérer pour la suite.

### Initialiser le cluster sur swarm-1

<code>sudo docker swarm join --token "Insérer le token du manager"</code>

### Initialiser le cluster sur swarm-2

<code>sudo docker swarm join --token "Insérer le token du manager"</code>

### Initialiser le cluster sur swarm-3

<code>sudo docker swarm join --token "Insérer le token du worker"</code>

### Initialiser le cluster sur swarm-4

<code>sudo docker swarm join --token "Insérer le token du worker"</code>

### Initialiser le cluster sur swarm-5

<code>sudo docker swarm join --token "Insérer le token du worker"</code>

### Vérifier le cluster

<code>sudo docker ls</code>

### Créer un réseau interne à partir de swarm-0

<code>sudo docker network create -d overlay net</code>

Ensuite, il faut lancer le proxy inverse avec Traefik :

<code>sudo mkdir -p /home/docker/swarm/</code>

<code>sudo nano /home/docker/swarm/traefik.yml</code>

À ce stade, il faut copier l'intégralité du fichier *traefik.yml* disponible dans le répertoire **app** du Github dans le fichier *traefik.yml* de votre machine.

### Déployer Traefik

<code>sudo docker stack deploy --compose-file=/home/docker/swarm/traefik.yml traefik</code>

En cas de besoin, vous pouvez retirer Traefik : <code>sudo docker stack rm traefik</code>

Dans votre navigateur, après 2 ou 3 minutes, le proxy inverse Traefik devrait être en fonction sur la machine swarm-0 sur le port 9090 : http://192.168.56.10:9090

### Déployer Drupal

Il faut créer le fichier de configuration Drupal à l'aide du fichier *docker-compose.yml* disponible dans le répertoire Github.
<code>sudo nano /home/docker/swarm/docker-compose.yml</code>

Il faut maintenant déployer le fichier *docker-compose.yml*.
<code>sudo docker stack deploy --compose-file=/home/docker/swarm/docker-compose.yml docker-compose</code>

En cas de besoin, vous pouvez retirer docker-compose : <code>sudo docker stack rm docker-compose</code>

### Vérifier l'installation

<code>sudo docker service ps docker-compose</code>

## Vous pouvez désormais lancer Drupal à votre adresse