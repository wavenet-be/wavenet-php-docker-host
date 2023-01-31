# Démarrage de l'image

## A chaque mise à jour de l'image
`docker-compose build`

## Pour démarrer les services
`docker-compose up -d`

# Utilisation
Le projet démarre :
- Une base de données MySql 3.7 ouverte sur le port 3306, utilisateur root, sans mot de passe
- Un container php 8.1 avec php mappé sur le répertoire /var/www/html et ouvert sur le port 8088