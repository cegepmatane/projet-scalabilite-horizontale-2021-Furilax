# Comment installer l'application avec Docker ?

### Récupérer l'image sur le Docker Hub

<code>sudo docker pull tmromain/projetscalabiliter:latest</code>

Cette commande permet de récupérer l'image docker grâce à l'adresse du Docker Hub.

### Exécuter l'image

<code>sudo docker run --name drupalinstall -p 8080:80 -d tmromain/projetscalabiliter</code>

Cette commande permet de construire et de l'exécuter l'image afin de déployer les programmes qu'elle contient.

### Autre commande pour exécuter l'image

<code>sudo docker start drupalinstall</code>

Cette commande permet de relancer l'image une fois que celle-ci est désactivée. En revanche, il faut qu'elle soit récupérée au préalable.
