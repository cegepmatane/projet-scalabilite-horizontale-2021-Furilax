# Projet Scalabilité Horizontale par Romain Dubard-Robert, Nicolas Rimbault et Matteo De Lutiis.

sudo docker pull tmromain/projetscalabiliter:latest : cette commande sert a recuperer l'image docker grace a l'adress du docker hub

sudo docker run --name drupalinstall -p 8080:80 -d tmromain/projetscalabiliter : permet de construire l'image docker

sudo docker start drupalinstall : cette commande permet de relancer l'image
