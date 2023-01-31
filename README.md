# Génération des images
## A chaque mise à jour de l'image
```bash
cd images\\wavenet-php
build.bat
```
**Est c'est quand une mise à jour de l'image ?**
- Quand une librairie a été ajoutée à l'image de base (aka : on a modifié le Dockerfile pour que vous ne deviez pas faire l'installation à la main)

## Pour démarrer les services
`docker-compose up -d`

# Utilisation
Le projet démarre :
- Une base de données MySql 3.7 ouverte sur le port 3306, utilisateur root, sans mot de passe
- Un container php 8.1 avec php mappé sur le répertoire /var/www/html et ouvert sur le port 8088

## Et en vrai, comment je travaille ?
PHP est up and running sur le répertoire  `/var/www/html` **du container**, cela veut dire qu'il y a plusieurs options :
- Se connecter en SSH sur le service, qui démarre sur le port 2222 avec le nom d'utilisateur `sshuser` et le mot de passe : `Changeme`, ensuite c'est comme travailler sur une Debian en ligne de commande :)
- Utiliser des outils comme VsCode qui peuvet se connecter directement sur le container et éditer les fichiers
- Utiliser des fonctionnalités comme le "Remote Development" de JetBrains qui peut se connecter en SSH et développer à distance
- Utiliser un outil comme *SFTP Drive !* qui peut se connecter et monter un répertoire SFTP comme lecteur Windows (l'édition starter est suffisante) : https://www.nsoftware.com/sftp/drive/download.aspx