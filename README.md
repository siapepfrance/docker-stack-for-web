# Stack docker pour projets webs (supporte Symfony, php et les spa)

#### Docker Compose

Le fichier docker-compose.yml une infrastructure as code contenant des exemples

pour le déploiement de projets Symfony 3 à 6, php 7, php 8 et une spa.

- - - - - - - - - - - - - - - - - - - - - -

Pour ajouter un projet dans votre infrastructure réelle, il faut :

-> 1 - Dupliquer les services que vous souhaites

-> 2 - Modifier le volume des services dupliqués afin qu'ils pointent vers le bon projet.

-> 3 - Modifier le port des service dupliqués.

-> 4 - S'il le faut ajuster les variables d'envuronnement se trouvant dans les fichiers .env.php.local, .env.nginx-*.local.

#### PHP 8.4

Une image php dédiée est disponible dans le dossier [php-84](./php-84)

Celle-ci peut être ajoutée à vos projets compatibles symfony 7+ ou php 8.4+ en utilisant l'image => siapep/php-84

#### PHP 8.2

Une image php dédiée est disponible dans le dossier [php-82](./php-82)

Celle-ci peut être ajoutée à vos projets compatibles symfony 4+ ou php 8+ en utilisant l'image => siapep/php-82

#### PHP 7.3 (projets php legacy)

Une image php dédiée est disponible dans le dossier [php-73](./php-73)

Celle-ci peut être ajoutée à vos projets compatibles symfony 3 ou php 7+ en utilisant l'image => siapep/php-73

#### NGINX 1.21 pour php

Une image nginx dédiée aux applications php est disponible dans le dossier [nginx-php](./nginx-php)

Celle-ci peut être ajoutée à vos projets en utilisant l'image => siapep/nginx-php

#### NGINX 1.21 pour les spa

Une image nginx dédiée aux single page applications est disponible dans le dossier [nginx-spa](./nginx-spa)

Celle-ci peut être ajoutée à vos projets en utilisant l'image => siapep/nginx-spa