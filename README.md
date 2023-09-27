# Stack docker pour Symfony 6

#### Docker Compose

Le fichier docker-compose.yml contient un exemple d'infrastructure as code

pour le déploiement d'un projet Symfony 6 avec les deux images php et nginx.

- - - - - - - - - - - - - - - - - - - - - -

Pour ajouter d'autres projets Symfony 6 dans votre infrastructure, il faut :

-> 1 - Dupliquer les services php et nginx.

-> 2 - Modifier le volume des services dupliqués afin qu'ils pointent vers le nouveau projet.

-> 3 - Modifier le port du service nginx dupliqué.

-> 4 - S'il le faut ajuster les variables d'envuronnement se trouvant dans les fichiers .env.php.local, .env.nginx.local.

#### PHP 8.2

Une image php dédiée est disponible dans le dossier [PHP](./php)

Celle-ci peut être ajoutée à vos projets compatibles symfony 6 ou php 8+ en utilisant l'image => siapep/php-for-symfony-6

#### PHP 7.3 (projets php legacy)

Une image php dédiée est disponible dans le dossier [PHP-73](./php-73)

Celle-ci peut être ajoutée à vos projets compatibles symfony 3 ou php 7+ en utilisant l'image => siapep/php-for-symfony-3

#### NGINX 1.21

Une image php dédiée est disponible dans le dossier [NGINX](./nginx)

Celle-ci peut être ajoutée à vos projets en utilisant l'image => siapep/nginx-for-symfony-6

#### Extra : base de données

Si vous souhaitez connecter une base de données à votre projet Symfony,

plusieurs solutions s'offrent à vous :

-> Connecter une base de donnée se trouvant sur la machine hôte à votre conteneur.

Dans ce cas, il suffit dans le fichier .env ou .env.local de votre projet Symfony

et renseigner mysql://root:@host.docker.internal:3306 au lieu de mysql://root:@127.0.0.1:3306 dans la variable DATABASE_URL.


-> Connecter une base de données distante. Pour cela il suffit de rebseigner les 

informations classiques de votre base de données.


-> Connecter une base de donnée conteneurisée. Pour cela il vous suffit d'ajouter 

l'image de votre base de données dans le fichier docker-compose.yml et de connecter

votre conteneur php au conteneur de la base de données en paramétrant un réseau 

commun pour les deux services.