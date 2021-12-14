# Comment installer l'application avec Docker ?

## Installation Drupal

### Récupérer l'image sur le Docker Hub

<code>sudo docker pull tmromain/projetscalabiliter:latest</code>

Cette commande permet de récupérer l'image docker grâce à l'adresse du Docker Hub.

### Exécuter l'image

<code>sudo docker run --name drupalinstall -p 8080:80 -d tmromain/projetscalabiliter</code>

Cette commande permet de construire et de l'exécuter l'image afin de déployer les programmes qu'elle contient.

### Autre commande pour exécuter l'image

<code>sudo docker start drupalinstall</code>

Cette commande permet de relancer l'image une fois que celle-ci est désactivée. En revanche, il faut qu'elle soit récupérée au préalable.


## Installation Mysql

### Récupérer l'image de mysql 

<code>sudo docker pull mysql</code>

Cette image permet de connecter drupal a MYSQL

### Build et lancer l'image en container

<code> sudo docker run -d --name some-mysql-drupal -e MYSQL_DATABASE=drupal  -e MYSQL_USER=user -e MYSQL_PASSWORD=password  -e MYSQL_ROOT_PASSWORD=password mysql </code>

Permet de lancer l'image avec des information de connexion pour drupal

<code> sudo docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' some-mysql-drupal </code>

Recuperer l'ip qui nous sera utile plus tard.

### Faire des changement dans mysql

<code>sudo docker exec -it some-mysql-drupal bash</code>

Cette commande permet de se connecter au container

<code># mysql -h localhost -u root -p</code>

Permet de se connecter a mysql


<code>CREATE DATABASE drupaldb;</code>

Crée la base de données qui sera utiliser par drupal 

<code>CREATE USER 'drupal'@'172.17.0.2' IDENTIFIED BY 'password';</code>

Creer l'utilisateur drupal assosier à son ip

<code>GRANT ALL PRIVILEGES ON *.* TO 'drupal'@'172.17.0.2';</code>

Donne tout les privillége a cette utilisateur drupal

![image](https://user-images.githubusercontent.com/54318639/146091250-a866a19a-2f0a-4c59-b7f1-12c3ece21405.png)

Faire cette configuration
