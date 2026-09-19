# NovaStar LED Offset

Application web installable (PWA) pour préparer les offsets `Start X` / `Start Y`
d'écrans LED NovaStar.

## Fonctions

- saisie des zones en millimètres, pixels ou bandes LED ;
- bandes de 20 cm et 25 cm mélangeables et plaçables à gauche ou à droite ;
- conversion par pitch, calcul des vides et des offsets ;
- affectation d'un port RJ45 et du sens d'entrée pour chaque écran ;
- chaînage de plusieurs écrans sur un même port ;
- schéma Complex Screen lisible sur mobile, exportable en SVG et PNG ;
- rappel des capacités maximales des contrôleurs NovaStar MCTRL et VX ;
- fonctionnement hors ligne après une première ouverture en HTTPS.

Les décimales peuvent être saisies avec une virgule ou un point.

## Mise en ligne avec GitHub Pages

1. Placer les fichiers de ce dossier à la racine du dépôt GitHub.
2. Dans **Settings → Pages**, choisir **Deploy from a branch**.
3. Sélectionner la branche principale et le dossier `/ (root)`.
4. Ouvrir l'adresse HTTPS fournie par GitHub Pages.

Sur Android, utiliser le bouton **Installer l'application** ou le menu de Chrome.
Une PWA ne s'installe pas normalement depuis une adresse `file://`.

## Fichiers

- `index.html` : interface et calculs ;
- `manifest.webmanifest` : métadonnées d'installation ;
- `sw.js` : cache hors ligne ;
- `icon-192.png` et `icon-512.png` : icônes de l'application.
