# Notes des TP Docker


## TP 1 - lancer ton premier conteneur


### Mes commentaires:

-	Après l'exécution de la commande docker run hello-world, j’ai vu le message « Hello from Docker ! » s'afficher. De plus après ce message les informations fournies nous indiquent que le client Docker a communiqué avec le daemon Docker, que l'image hello-world a été téléchargée depuis Docker Hub, puis qu'un conteneur a été créé et exécuté avec succès. Ce test m’a permis de vérifier le bon fonctionnement de l'installation Docker mais aussi comprendre le mécanisme derrière la création de ce message.

-	L'exécution de la commande docker ps -a a affiché la liste de tous les conteneurs présents sur le système, qu'ils soient actifs ou arrêtés. Les informations affichées incluent notamment l'identifiant du conteneur, l'image utilisée, la commande exécutée, la date de création, le statut et le nom du conteneur. Cette commande permet d'avoir une vue d'ensemble des conteneurs disponibles sur la machine.


---

## TP 2 - lancer un serveur web et l’a cher

### Mes commentaires :

- Dans ce TP2, nous avons commencé par lancer un conteneur Nginx à l’aide de la commande docker run -d -p 8080:80 --name montest nginx. Cette commande permet de rediriger le port 8080 de la machine hôte vers le port 80 du conteneur, sur lequel Nginx écoute par défaut. Ainsi, lorsque j’accède à l’adresse http://localhost:8080 affiche la page d’accueil de Nginx.

- Ensuite, la commande docker logs montest a été utilisée afin d’afficher les journaux du conteneur et suivre son activité.Enfin, le conteneur a été arrêté avec docker stop montest, puis supprimé avec docker rm montest.

- Ce TP2 m’a permis de comprendre le principe de mapping des ports, notamment à travers la redirection entre le port de la machine hôte et celui du conteneur.


---
## TP 3 - entrer dans un conteneur


### Mes commentaires :

- Dans ce TP3, nous avons exécuté la commande docker run -d --name montest2 nginx afin de créer et lancer un conteneur basé sur l’image Nginx.Ensuite, la commande docker exec -it montest2 sh a été utilisée pour ouvrir un terminal à l’intérieur du conteneur. Une fois connecté, nous avons accédé au répertoire web par défaut de Nginx et affiché son contenu à l’aide de la commande ls. L’exécution de cette commande a permis de constater la présence de deux fichiers principaux : 50x.html, correspondant aux pages d’erreur, et index.html, représentant la page d’accueil de Nginx.

- Enfin, le conteneur a été arrêté et supprimé à l’aide de la commande docker rm -f montest2, afin de nettoyer l’environnement.

- Ce TP3 m’a permis de comprendre comment accéder à un conteneur et exécuter des commandes à l’intérieur de celui-ci.


---
## TP 4 - créer ta propre image avec un Dockerfile


### Mes commentaires :

- Dans ce TP4, j’ai créé un fichier index.html contenant le titre « Ma première image Docker », ainsi qu’un Dockerfile faisant référence à ce fichier. Ensuite, j’ai construit une image Docker à l’aide de la commande docker build -t mon-site .. Cette image intègre le contenu de la page web dans une image basée sur Nginx.

- J’ai ensuite lancé un conteneur avec la commande docker run -d -p 8080:80 --name monsite mon-site. Cette commande permet de rediriger le port 8080 de ma machine hôte vers le port 80 du conteneur, sur lequel Nginx sert la page web. En accédant à l’adresse http://localhost:8080, j’ai pu afficher le titre « Ma première image Docker », ce qui confirme le bon fonctionnement de l’image que j’ai créée.

- Enfin, j’ai supprimé le conteneur à l’aide de la commande docker rm -f monsite.

- Ce TP m’a permis de mettre en pratique la création d’une image Docker à partir d’un Dockerfile, ainsi que le déploiement et le test d’un conteneur contenant une application web personnalisée.


---
## TP 5 - utiliser docker compose


### Mes commentaires :

- Dans ce TP5, j’ai créé un dossier dockerTest, dans lequel j’ai mis en place un fichier docker-compose.yaml. Ce fichier permet de définir un service basé sur l’image Nginx et de configurer la redirection du port 8080 de la machine hôte vers le port 80 du conteneur, qui correspond au port d’écoute par défaut de Nginx.

- À travers ce TP 5 , j’ai découvert une autre manière de déployer un conteneur en utilisant Docker Compose, qui permet de simplifier la configuration et l’exécution des services via un fichier de configuration unique.

