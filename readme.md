# Initialisation du projet

Dans un premier temps copie le `docker-compose.override.example.yml` vers `docker-compose.override.yml`

```bash
cp docker-compose.override.example.yml docker-compose.override.yml
```

Ensuite, pour lancer l'application, il vas falloir générer une clé a l'aide de php artisan. 

```bash
docker run -it --rm --entrypoint /bin/bash lscr.io/linuxserver/bookstack:latest appkey
```

Cette clé il faut la rajouter dans le fichier `docker-compose.override.yml` au niveau de la varaible d'environement `APP_KEY`.  
Ensuite, il vas falloir que tu modifie la variable `APP_URL` avec ton nom de domain, car c'est ce qui vas permettre d'accéder à ton application.  
Il va aussi falloir que tu modifie les `PUID` et les `PGID` avec celui de ton utilisateur avec lequel tu les lances. `id` vas te permettre d'obtenir ses chiffres.
Et enfin, il faut modifier les mots de passer car il ne faut jamais laisser les mots de passe par défaut.

# Lancement de la stack 

Tu vas pouvoir lancer la stack avec cette commande : 

```bash
docker compose up -d
```

Tu peux vérifier que le lancement c'est bien passé avec les commandes suivante :

```bash
docker compose ps
docker compose logs
```