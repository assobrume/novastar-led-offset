# NovaStar LED Offset

> Version BÊTA : prise en charge expérimentale des écrans avec boîtiers de contrôle en haut et en bas.

La bêta comprend également la sauvegarde automatique, les configurations nommées,
l’export/import JSON et la duplication complète d’un écran.
Les panneaux de configurations et de capacités sont repliables sur mobile comme sur ordinateur.

Application web installable (PWA) pour préparer les offsets `Start X` / `Start Y`
d'écrans LED NovaStar.

## Fonctions

- historique des modifications : boutons Annuler/Rétablir et raccourcis Ctrl+Z/Ctrl+Maj+Z (ou Cmd sur Mac), jusqu’à 40 étapes pendant la session ;

- export expérimental `.scr` du Complex Screen depuis les bandes, à contrôler dans NovaLCT avant toute transmission au matériel ;
- les zones Profuse divisées restent regroupées ; une alerte compare la taille recalculée à la taille initiale après les retouches, vides intérieurs compris ;
- l’alerte de taille apparaît directement sur chaque sous-zone concernée ; les groupes antérieurs sans taille initiale prennent leur taille actuelle comme référence ;
- nom du groupe Profuse modifiable dans le récapitulatif, partagé par les sous-zones et enregistré avec le projet ;

- mode rapide Profuse avec X, Y, largeur et hauteur de chaque zone, plus le format du média étendu ;
- division rapide d’une zone Profuse en 2, 3, 4, 5 ou davantage de zones ; le total de pixels est conservé et les noms Zone 1, Zone 2… suivent l’ordre ;
- dimensions de chaque zone modifiables après division, avec hauteur/largeur propre facultative et vide entre chaque zone en millimètres ;
- menu compact « ⋯ » disponible sur une zone repliée pour diviser, dupliquer ou supprimer ;
- schéma Profuse proportionnel sur les axes X et Y, avec origine et dimensions prêtes à reporter ;
- zones écran repliables, avec icônes de duplication et de suppression accessibles même fermées ;
- confirmation nominative avant suppression et protection de la dernière zone ;
- bouton « Tout replier / Tout ouvrir » et réorganisation en tête de liste, utilisable au toucher, à la souris ou avec les flèches du clavier ;
- toutes les grandes sections sont refermables ; leur état est conservé dans le brouillon, les configurations et les exports JSON ;
- calcul automatique à chaque saisie, sans bouton Calculer, y compris lorsque les résultats sont repliés ;
- déclaration de la vue de saisie, puis conversion miroir volontaire : ordre des écrans, vides, arrivées RJ45 et placement gauche/droite des bandes inversés ;
- récapitulatif NovaLCT compact sans défilement horizontal sur mobile ;
- tableau NovaLCT généré bande par bande : Sending Card, Port, Starting X/Y, Width et Height ;
- contrôle de l’origine média `X=0 / Y=0` et avertissement si la vue arrière est encore active ;
- affichage du tableau NovaLCT par position physique croissante, l’identification des Receiving Cards restant gérée par NovaLCT ;
- déduction automatique des bandes depuis une résolution, avec priorité aux bandes de 25 cm à précision égale ;
- saisie des zones en millimètres, pixels ou bandes LED ;
- bandes de 20 cm et 25 cm mélangeables, avec placement gauche, droite ou personnalisé autour des bandes centrales ;
- conversion par pitch, calcul des vides et des offsets ;
- affectation d'un port RJ45 et du sens d'entrée pour chaque écran ;
- chaînage de plusieurs écrans sur un même port ;
- schéma Complex Screen lisible sur mobile, exportable en SVG et PNG ;
- rappel des capacités maximales des contrôleurs NovaStar MCTRL et VX ;
- fonctionnement hors ligne après une première ouverture en HTTPS.

Les décimales peuvent être saisies avec une virgule ou un point.
Pour diviser une zone Profuse, ouvre son menu « ⋯ », choisis le nombre de parties puis modifie les mesures et les champs « Vide après » selon le chantier. Le vide précédemment situé après la zone reste après la dernière partie.

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

Les groupes Profuse sont encadrés sur le schéma avec la couleur reprise près de leur nom. Les ports 1 et 2 du schéma NovaStar utilisent respectivement vert et jaune ocre, comme les repères NovaLCT ; les numéros de port restent la référence.

Nouveau projet / Réinitialiser : confirmation, retour aux réglages par défaut avec une seule zone à renseigner, mode actuel conservé. Les configurations enregistrées restent disponibles et la réinitialisation peut être annulée.
