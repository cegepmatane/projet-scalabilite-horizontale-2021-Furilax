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

Il faut 



<code></code>
<code></code>
<code></code>
<code></code>
<code></code>
<code></code>
<code></code>
<code></code>
<code></code>
<code></code>