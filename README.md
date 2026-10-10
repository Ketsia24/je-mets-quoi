# Je mets quoi ?

La tenue du jour selon la météo de ton créneau dehors.

On choisit un lieu, un créneau (par exemple 8h → 19h), un profil (frileux, normal, peu frileux) et un trajet (à pied ou à vélo). L'outil lit la météo heure par heure et rend une tenue complète, couche par couche, avec la raison chiffrée de chaque choix et le numéro de la règle qui l'a décidée.

Projet réalisé entièrement avec une IA (Claude), sans écrire de code à la main : le travail a consisté à formuler les demandes, critiquer les résultats et trancher entre les options.

## Utiliser l'outil

- **En ligne, météo en direct** : https://ketsia24.github.io/je-mets-quoi/ (une fois GitHub Pages activé : Settings → Pages → branche `main`, dossier racine).
- **Sur son ordinateur** : télécharger `index.html` et l'ouvrir dans un navigateur, connecté à Internet.
- **Aperçu sans installation** : [page Claude](https://claude.ai/artifact/CPdbcb7NoPH9RsnGazf6uB), sur des journées d'exemple.

Quand les services météo ne sont pas joignables, la page passe en **mode exemple** : trois journées fictives (automne, été, hiver), clairement signalées.

## Ce que fait l'outil

- **Ciel du jour** : le verdict en grand, sur un ciel qui suit la météo du créneau.
- **Repères** : comparaison avec hier, avec la même semaine des 10 dernières années, et parapluie à prévoir pour demain.
- **Ta tenue, couche par couche** : haut, par-dessus, veste, bas, chaussures, chacun avec sa raison.
- **À emporter** et **À surveiller** : accessoires et alertes (orage, verglas, vent, air, pollens, humidité).
- **Heure par heure** : bande horaire, courbe du ressenti et risque de pluie, tableau des données.
- **Les règles de recommandation** : 49 règles fixes et numérotées, avec celles appliquées aujourd'hui.
- **Carte** : le lieu choisi ; un clic choisit un autre point.

## Sources de données

Toutes gratuites pour un usage non commercial, sans clé, via [Open-Meteo](https://open-meteo.com/) :

| Données | Source |
| --- | --- |
| Prévisions heure par heure (température, ressenti, humidité, pluie, vent) | modèles Météo-France AROME et ARPEGE |
| Probabilité de pluie et indice UV | meilleur modèle disponible d'Open-Meteo |
| Normales de saison (10 dernières années) | réanalyse ERA5 (Copernicus) |
| Qualité de l'air et pollens | CAMS Europe (Copernicus) |
| Recherche de villes | GeoNames |
| Fond de carte | © contributeurs [OpenStreetMap](https://www.openstreetmap.org/copyright), affiché avec Leaflet |
| Contours des pays (mode exemple) | Natural Earth |

L'API officielle du portail Météo-France n'est pas utilisée : elle demande un identifiant secret, qui serait visible dans une page publique.

## Règles de recommandation

La tenue sort de 49 règles fixes, écrites à l'avance et numérotées par famille : couches (C), pluie (P), humidité (H), vent (V), froid (F), soleil et chaleur (S), repères (R), sécurité (A). Quelques exemples :

| Règle | Si… | Alors… |
| --- | --- | --- |
| C3 | ressenti le plus froid du créneau entre 6° et 11° | veste mi-saison |
| P1 | risque de pluie ≥ 50 % sur une heure, ou cumul ≥ 1 mm | parapluie et veste imperméable |
| P6 | demain, risque de pluie ≥ 30 % sur le même créneau | préparer le parapluie dès la veille |
| H1 | chaleur humide : ≥ 22° et ≥ 70 % d'humidité | s'habiller plus léger (coton, lin) |
| H2 | froid humide : ≤ 10° et ≥ 85 % d'humidité | laine et veste fermée |
| R3 | journée ≥ 3° plus froide que la normale | se couvrir plus que d'habitude |

La grille complète est affichée dans l'outil et dans le dossier de projet.

## Documents

- [`docs/Je-mets-quoi-Dossier-de-projet.docx`](docs/Je-mets-quoi-Dossier-de-projet.docx) : la démarche (sujet, API, décisions tranchées, journal des prompts, règles, limites, pistes).
- [`docs/Je-mets-quoi-Documentation.docx`](docs/Je-mets-quoi-Documentation.docx) : à quoi sert chaque outil, chaque donnée et chaque bloc, et pourquoi ces choix.

## Limites

Conseils indicatifs calculés à partir de prévisions, qui se trompent parfois, surtout en fin de journée. La sensation de froid varie d'une personne à l'autre ; les réglages de profil sont des approximations.

## Crédits

Données météo : [Open-Meteo.com](https://open-meteo.com/) (CC BY 4.0), modèles Météo-France, réanalyse ERA5 et CAMS (Copernicus). Lieux : GeoNames. Carte : © contributeurs OpenStreetMap, bibliothèque [Leaflet](https://leafletjs.com/). Contours des pays : Natural Earth. Polices : Google Fonts.
