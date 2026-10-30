# Turf Acher — prototype PWA

## Ce que contient cette version
- Interface mobile adaptée à Safari iPhone.
- Classement statistique indépendant basé sur les données renseignées.
- Import/export JSON, ajout manuel de chevaux et sauvegarde locale dans le navigateur.
- Démonstration fictive clairement identifiée.
- Tentative de récupération du programme PMU public (non officielle, non garantie et susceptible d'être bloquée par CORS).
- Mise en cache PWA pour une utilisation hors connexion après première visite.

## Installation sur iPhone
Une PWA doit être servie en HTTPS pour être installée correctement :
1. Déposez ces trois fichiers sur un hébergement statique HTTPS gratuit (par exemple GitHub Pages).
2. Ouvrez l'adresse du site dans Safari sur l'iPhone.
3. Touchez Partager > Sur l'écran d'accueil > Ajouter.

## Lancer en local sur un ordinateur
Dans le dossier, lancez un serveur HTTP, par exemple :
`python3 -m http.server 8000`
Puis ouvrez `http://localhost:8000`.
Pour installer sur iPhone, localhost sur le PC ne suffit pas : il faut HTTPS public ou un serveur accessible via HTTPS.

## Données
L'interface ne prétend pas accéder à des flux garantis en temps réel. Le point d'accès PMU utilisé est non documenté officiellement et peut changer ou bloquer les requêtes navigateur. Open PMU API est principalement utile pour les arrivées historiques. Import JSON possible si la récupération directe échoue.

## Format JSON accepté
```json
{
  "races": [
    {
      "id": "R1C1",
      "meeting": "R1",
      "number": 1,
      "name": "Prix exemple",
      "track": "Hippodrome",
      "distance": 2100,
      "discipline": "Trot attelé",
      "horses": [
        {
          "number": 4,
          "name": "Cheval exemple",
          "music": "1a 2a 3a 0a",
          "earnings": 45000,
          "age": 6,
          "jockey": "Nom"
        }
      ]
    }
  ]
}
```

## Important
Le score est une heuristique expérimentale, pas une probabilité calibrée. Les critères jockey, corde, poids, piste, distance et météo ne sont pas encore inclus faute de données structurées fiables dans cette première version. Ne misez jamais une somme que vous ne pouvez pas perdre.
