# FASO ORAL

Plateforme web de collecte, conservation, valorisation et transmission du patrimoine oral du Burkina Faso.

> Version 0.1, socle fonctionnel. Les contenus livrés avec le dépôt sont des **données de démonstration fictives**, signalées comme telles partout dans l'interface (badge « DÉMO ») et en base (`is_demo = true`). Aucun récit de démonstration ne doit être présenté comme authentique.

## Contenu du dépôt

| Dossier | Rôle |
| --- | --- |
| `backend/` | API REST Node.js + Express + TypeScript, PostgreSQL, stockage local ou S3, Swagger |
| `frontend/` | Application React + TypeScript + Tailwind CSS + Leaflet |
| `docs/` | Architecture, base de données, API, sécurité, éthique des contenus, installation, déploiement, feuille de route |
| `docker-compose.yml` | PostgreSQL, MinIO (S3), Mailpit (e-mails de test), API, frontend |

## Démarrage rapide (Docker)

```bash
cp .env.example .env          # puis renseigner les secrets (voir docs/INSTALLATION.md)
docker compose up -d --build
docker compose exec api npm run db:migrate
docker compose exec api npm run db:seed      # admin + données de démonstration
```

- Frontend : http://localhost:8080
- API : http://localhost:8080/api (relayée par Nginx ; aussi joignable directement sur le port 4000)
- Documentation Swagger : http://localhost:8080/api/docs
- Boîte e-mail de test (Mailpit) : http://localhost:8025

Installation sans Docker, variables d'environnement et déploiement : voir `docs/INSTALLATION.md` et `docs/DEPLOIEMENT.md`.

## Fonctionnalités de la v0.1

- Comptes : inscription, connexion, déconnexion, réinitialisation du mot de passe par e-mail, profil, rôles (visiteur, utilisateur, contributeur, administrateur).
- Carte interactive des 17 régions (découpage de juillet 2025) avec filtres et fiches culturelles.
- Bibliothèque de récits : recherche plein texte en français, filtres multicritères, fiches détaillées.
- Lecteur audio multilingue (version originale / version française), téléchargement selon les droits.
- Bibliothèque vidéo : lecteur, sous-titres WebVTT, transcriptions, signalement des reconstitutions.
- Expérience narrative pas à pas (scènes, images, audio synchronisé par horodatage).
- Contributions avec audio, vidéo, image, informations sur le dépositaire et consentement obligatoire.
- Circuit de validation : rien n'est publié sans décision d'un administrateur.
- Notifications aux administrateurs (in-app + e-mail) à chaque contribution.
- Demandes de retrait par les dépositaires ou ayants droit.
- Tableau de bord administrateur : récits, médias, vidéos, référentiels, utilisateurs, statistiques.

## Licence du code

À définir par le porteur du projet. Les contenus culturels relèvent des droits de leurs dépositaires et communautés (voir `docs/CONTENU_ET_ETHIQUE.md`).

## Documentation

| Document | Contenu |
| --- | --- |
| [Architecture](docs/ARCHITECTURE.md) | analyse des besoins, choix techniques justifiés, arborescence complète |
| [Base de données](docs/BASE_DE_DONNEES.md) | schéma relationnel, contraintes, règles métier |
| [API](docs/API.md) | conventions, authentification, routes (détail dans Swagger) |
| [Sécurité](docs/SECURITE.md) | mesures et tests |
| [Contenu et éthique](docs/CONTENU_ET_ETHIQUE.md) | authenticité, consentement, retrait |
| [Données géographiques](docs/DONNEES_GEOGRAPHIQUES.md) | 17 régions, import des contours officiels |
| [Installation](docs/INSTALLATION.md) | lancement local et scénario de test |
| [Déploiement](docs/DEPLOIEMENT.md) | serveur, HTTPS, services gérés, sauvegardes |
| [Feuille de route](docs/FEUILLE_DE_ROUTE.md) | avancement par étape, limites, phase 2 |
