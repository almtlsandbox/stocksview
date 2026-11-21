# Suivi de portefeuille

Application web d'une seule page pour suivre des actions achetées (titres américains et canadiens) : gains et pertes, code de couleur, alertes, regroupement par compte (REER, CELI, NR…), étiquettes et graphiques.

## Utilisation

1. Ouvre `index.html` dans Chrome ou Edge (double-clic).
2. Obtiens une clé gratuite sur [alphavantage.co](https://www.alphavantage.co/support/#api-key) et colle-la dans **Réglages**.
3. Ajoute tes positions : symbole (`AAPL`, `SHOP.TO`, `XYZ.V`), quantité, date d'achat, prix payé (facultatif), compte et étiquettes.
4. Dans **Sauvegarde**, choisis un fichier `portefeuille.json` (idéalement dans OneDrive, Dropbox ou Google Drive) pour la sauvegarde automatique.

## Fonctionnement

- **Prix :** API Alpha Vantage (`TIME_SERIES_DAILY`, 1 appel par titre, qui donne aussi les ~100 dernières clôtures). Le plan gratuit permet environ 25 appels par jour ; au-delà, l'app fait une rotation en rafraîchissant d'abord les prix les plus anciens.
- **Devises :** titres `.TO`, `.V` en CAD, les autres en USD ; totaux convertis au taux de change actuel.
- **Données :** gardées dans le navigateur (localStorage) et, dans Chrome/Edge, écrites automatiquement dans le fichier de sauvegarde choisi. La clé API n'est jamais écrite dans ce fichier.
- **Historique :** les clôtures récupérées s'accumulent localement et alimentent les graphiques (gain en $ et performance relative en %).

Aucune dépendance ni serveur : tout est dans `index.html`.
