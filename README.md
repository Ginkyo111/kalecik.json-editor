# Kalecik.json editor

Éditeur de cartes pour **Kalecik** : génère un archipel (îles, relief, lacs, rivières, végétation), l'affiche en 2D et en 3D, puis l'exporte en JSON.

Application web 100 % statique : aucun serveur, aucune dépendance, aucune étape de build. Pensée pour les navigateurs mobiles (Android / iOS).

## Fonctionnalités

- Types de terrain : Archipel, Plaine, Hautes terres
- Curseurs de relief, côtes, montagnes, lacs, rivières et végétation (rochers, feuillus, pins, buissons)
- Aperçu 2D et 3D (cycle jour/nuit, saisons, nuages, oiseaux), plein écran, export PNG
- Export JSON (avec compression des chunks)
- Interface en français, anglais, turc, espagnol et allemand

## Utilisation

Ouvrir `index.html` dans un navigateur, ou lancer un petit serveur local :

```bash
python3 -m http.server 8000   # puis http://localhost:8000
```

## Publication sur GitHub Pages

1. Créer le dépôt et pousser les fichiers sur la branche `main`.
2. **Settings → Pages → Build and deployment** : *Deploy from a branch*, branche `main`, dossier `/ (root)`.
3. Le site est disponible sur `https://<utilisateur>.github.io/<depot>/`.

## Structure

```
index.html        page, écran de démarrage, générateur (script #genSrc, exécuté dans un Web Worker)
css/style.css     feuille de style
js/clouds.js      nuages décoratifs de l'en-tête (bruit de Perlin)
js/app.js         interface, rendu 2D / 3D, export
.nojekyll         désactive Jekyll sur GitHub Pages
```

Le générateur est volontairement inclus dans `index.html` : son code sert à la fois au Web Worker et de secours sur le fil principal.

## Performances

- Génération dans un Web Worker, démarré dès l'ouverture de la page
- Préchargement de la 3D (maillages, ombres, reflets) au passage en mode 3D
- Rendu 3D logiciel (canvas 2D) avec régulateur de résolution pendant les gestes ; en plein écran, résolution native de l'écran (budget `FS_PX` dans `js/app.js`)

## Licence

À définir par l'auteur (ajouter un fichier `LICENSE`).
