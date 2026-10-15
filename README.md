# NovaStar LED Offset

Application web installable pour préparer les zones et décalages d’écrans LED.

## Utilisation

- Mode complet NovaStar : bandes de 20/25 cm, ports RJ45, sens d’entrée, tableau de coordonnées et export expérimental `.scr`.
- Mode rapide : dimensions des zones en mm ou pixels, division, vides et groupes nommés. Ses calculs sont indépendants des réglages des bandes et des boîtiers.
- Calculs automatiques, zones et panneaux repliables, duplication et réorganisation.
- Annuler/Rétablir : boutons ou Ctrl+Z / Ctrl+Maj+Z (Cmd sur Mac), jusqu’à 40 états pendant la session. Dans un champ texte, le raccourci utilise l’annulation native du champ.
- Nouveau projet : confirmation, une zone vierge, sauvegardes nommées conservées. La remise à zéro est annulable.

## Schéma et dimensions

Le schéma complet utilise une échelle commune en millimètres : formats nominaux de 200/250 mm pour la largeur des bandes et pixels × pitch pour leur longueur. Les vides utilisent leur mesure en mm. Les cotes sont placées autour des écrans. Les dimensions physiques réelles peuvent différer, par exemple pour une bande mesurée à 195 mm : les formats nominaux restent une estimation.

Le schéma rapide représente le canvas en pixels. Les groupes ont un encadrement coloré et une alerte lorsque leur dimension totale change, vides intérieurs compris. La référence d’un ancien groupe dépourvu de dimension initiale est sa dimension au chargement.

La conversion face/arrière est volontaire. Elle transforme les côtés et l’ordre horizontal, en conservant les numéros de ports associés au matériel. Les écrans disposés sur Y gardent leur ordre vertical.

Les exports SVG et PNG gardent un fond blanc.

## Passage entre les modes

Le passage complet → rapide → complet conserve les dimensions X/Y. Au retour dans le mode complet, la saisie passe en pixels. Pour les doubles boîtiers, le total est réparti selon la proportion des deux parties. Pour un boîtier unique, le champ facultatif « Longueur des bandes de cet écran (px) » permet de conserver une longueur différente du réglage global. Les pixels de l’axe transversal doivent toujours correspondre aux bandes réellement installées pour un export SCR exact.

## Sauvegardes

Le brouillon et les configurations nommées sont stockés dans le navigateur. Ils ne sont pas synchronisés entre appareils. La dernière saisie est enregistrée au masquage ou à la fermeture de la page, sous réserve que le navigateur permette le stockage.

Exporter/importer un JSON permet de transférer les configurations. Il s’agit du format de cette application, pas d’un import natif dans un logiciel de diffusion.

## GitHub Pages et mise à jour

Téléverser les fichiers à la racine prévue par GitHub Pages, en remplaçant les fichiers de même nom. Ne pas téléverser le ZIP tel quel.

Pour une mise à jour de l’application, remplacer `index.html` et `sw.js`, ainsi que ce README pour la documentation. Les icônes et le manifeste ne sont à remplacer que s’ils ont changé. Fermer puis rouvrir l’application après le déploiement.

Conserver l’adresse du site et le navigateur pour retrouver les sauvegardes. Exporter les configurations JSON avant une mise à jour reste utile. Effacer les données du site supprime les sauvegardes locales.

## Vérification du 15 octobre 2026

- 117 scénarios principaux dans un DOM simulé sur les deux versions : 96 scénarios de zones rapides X/Y et unités, puis 21 configurations complètes avec génération SCR.
- Tests supplémentaires : division, retouches, groupes, duplication, noms réservés de sauvegarde, import invalide, reset/annulation, dernière saisie et rechargement.
- Tests ciblés : mélanges 20/25, conversions, échelle physique, ports, miroirs, liaisons et coordonnées SCR.
- Résolutions de bandes : entiers de 1 à 65 535 px. Nombres de bandes : entiers non négatifs. Les valeurs invalides effacent les résultats et bloquent l’export.
- Pas de validation tactile/visuelle dans un navigateur réel pendant cet audit. L’import des nouvelles orientations dans NovaLCT avec le matériel reste à contrôler avant transmission.

## Particularités bêta

Boîtier haut, bas, haut + bas, gauche, droite ou gauche + droite. Les configurations gauche/droite utilisent des bandes horizontales. Les deux parties peuvent avoir des longueurs différentes, saisies en mm ou pixels.

Avec deux boîtiers horizontaux sur le même port et des entrées opposées, le chemin part de l’entrée supérieure puis relie la sortie basse à l’entrée basse de l’autre côté. En miroir, cette liaison reste en bas.

**Limite connue :** les bandes verticales avec deux boîtiers sur l’axe Y ne sont pas prises en charge pour le tableau NovaLCT et le SCR. L’export est bloqué afin d’éviter des cartes superposées. Utiliser l’axe X pour cette configuration. Cette limite ne concerne pas les zones Y du mode rapide ni les bandes horizontales sur Y.

Vérification complémentaire : 63 aller-retour de mode dans les scénarios complets, contrôle des dimensions à chaque étape, modification en mode rapide et conservation au retour et après rechargement de configuration. Cas reproduit : 373 × 576 px reste 373 × 576 px.
