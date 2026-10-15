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
- les zones mode rapide divisées restent regroupées ; une alerte compare la taille recalculée à la taille initiale après les retouches, vides intérieurs compris ;
- l’alerte de taille apparaît directement sur chaque sous-zone concernée ; les groupes antérieurs sans taille initiale prennent leur taille actuelle comme référence ;
- nom du groupe mode rapide modifiable dans le récapitulatif, partagé par les sous-zones et enregistré avec le projet ;

- mode rapide mode rapide avec X, Y, largeur et hauteur de chaque zone, plus le format du média étendu ;
- division rapide d’une zone mode rapide en 2, 3, 4, 5 ou davantage de zones ; le total de pixels est conservé et les noms Zone 1, Zone 2… suivent l’ordre ;
- dimensions de chaque zone modifiables après division, avec hauteur/largeur propre facultative et vide entre chaque zone en millimètres ;
- menu compact « ⋯ » disponible sur une zone repliée pour diviser, dupliquer ou supprimer ;
- schéma mode rapide proportionnel sur les axes X et Y, avec origine et dimensions prêtes à reporter ;
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
Pour diviser une zone mode rapide, ouvre son menu « ⋯ », choisis le nombre de parties puis modifie les mesures et les champs « Vide après » selon le chantier. Le vide précédemment situé après la zone reste après la dernière partie.

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

Les groupes mode rapide sont encadrés sur le schéma avec la couleur reprise près de leur nom. Les ports 1 et 2 du schéma NovaStar utilisent respectivement vert et jaune ocre, comme les repères NovaLCT ; les numéros de port restent la référence.

Nouveau projet / Réinitialiser : confirmation, retour aux réglages par défaut avec une seule zone à renseigner, mode actuel conservé. Les configurations enregistrées restent disponibles et la réinitialisation peut être annulée.

Les hauteurs des parties haute et basse peuvent être saisies séparément en mm ou en pixels. La conversion mm → pixels utilise le pitch et arrondit au pixel entier. Les unités sont conservées dans les sauvegardes.

Bandes horizontales : boîtiers gauche, droite ou gauche + droite. La saisie principale décrit la hauteur empilée des bandes ; la longueur par défaut utilise le réglage global de longueur de bande. En double départ, les longueurs gauche/droite se saisissent séparément en mm ou px. Tableau NovaLCT, schéma et export SCR suivent cette orientation. Lors de la conversion face/arrière, les boîtiers changent de côté avec leurs paramètres et leur numéro de port.

Audit du 14 octobre 2026 : inversion verticale conserve l’ordre et les vides ; mélange 20/25 calculé plus rapidement ; import refuse les zones mal formées ; noms de sauvegardes compatibles avec les clés réservées ; message de suppression corrigé. Bêta : passage bandes/mm/px adapté aux bandes horizontales et largeur affichée correctement. Tests de calculs, groupes, historique, coordonnées SCR et inversion réussis. La vérification visuelle et tactile automatisée n’a pas pu être menée : Chromium plante au démarrage. Import NovaLCT sur matériel réel toujours à valider pour les nouvelles orientations.

Le schéma NovaStar inclut un détail coté pour chaque bande, en mm estimés à partir des pixels × pitch. Les détails sont hors échelle ; les mesures physiques doivent être vérifiées sur site. Les configurations doubles présentent séparément les deux parties.

Affichage des cotes simplifié : traits de largeur sous les écrans et hauteur sur le côté du schéma ; parties gauche/droite ou haute/basse séparées en double boîtier. Les miniatures de bandes ont été retirées.

Correction des cotes : l’axe empilé des bandes utilise les formats nominaux 200/250 mm, pas le pitch longitudinal. Exemple : 9 bandes de 25 cm = 2250 mm, 576 px si 64 px par bande. Les longueurs restent calculées par pixels × pitch. Bêta : les conversions mm/bandes/px et les vides sur l’axe Y horizontal utilisent cette distinction. Les formats nominaux ne remplacent pas une mesure physique (par exemple une bande réellement de 195 mm). Tests numériques et SCR passés ; rendu mobile et NovaLCT réel restent à vérifier.

Le schéma NovaStar respecte désormais une échelle commune en mm : bandes empilées nominales 200/250 mm, longueurs calculées avec le pitch, vides mesurés en mm. Les coordonnées et exports NovaLCT restent en pixels.

Correction liaison RJ45 horizontale : en double boîtier sur le même port avec entrées opposées, le chemin commence par le boîtier dont l’entrée est en haut. La liaison sortie basse → entrée basse reste en bas lors du miroir ; ordre des cartes exportées et tableau alignés sur ce chemin. Deux ports distincts restent deux départs indépendants.

Les libellés visibles utilisent désormais « Mode rapide ». Les identifiants internes des sauvegardes sont conservés.

Correction mode rapide : lors du passage depuis le mode complet, chaque zone reprend les dimensions X/Y calculées (y compris les bandes horizontales et doubles boîtiers), avec conversion en mm si nécessaire pour conserver les pixels. La restauration des sauvegardes et l’annulation ne déclenchent pas cette conversion. Tests de transition X/Y, mm/px/bandes, groupes, calculs et génération SVG passés.
