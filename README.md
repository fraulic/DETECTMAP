# Détect'Map Pro — Spécifications Techniques & Cadrage

Ce document consacre l'expression globale des besoins et l'architecture fonctionnelle de la solution privée de cartographie sur-mesure Détect'Map, optimisée pour l'iPhone 17 Pro Max.

## 1. Principes Fondamentaux & Souveraineté
- **Confidentialité Absolue :** Aucune donnée n'est transmise à un serveur distant ou à un Cloud tiers. L'intégralité des tracés et des positions de cibles reste confinée au sein du stockage local matériel de l'appareil (LocalStorage).
- **Autonomie Énergétique :** L'application est nativement compatible avec le Mode Avion. La puce GPS opère de manière passive en tâche de fond (intervalles de calcul calés sur la marche lente de détection) pour économiser la batterie.

## 2. Architecture Ergonomique (Bichromie & Accessibilité)
L'interface applique une charte graphique Flat stricte, monochrome et hautement contrastée, spécifiquement étudiée pour être lue sur le terrain sans lunettes de près.
- **Header (8%) :** Outils de gestion de fichiers (.json) pour l'import/export souverain et accès aux documentations cumulées.
- **Carte (84%) :** Zone cartographique maximale.
- **Footer (8%) :** Panneau de commande unifié doté de 4 boutons tactiles de grande taille (PLAY, CIBLE, FOCUS, CARTES).

## 3. Spécifications Cartographiques & Superposition (cartes.gouv.fr)
Le moteur graphique s'appuie sur les flux WMTS sécurisés du portail d'État français (IGN - Géopf). L'application gère l'empilement simultané ("sandwiche") et l'opacité individuelle des couches via des curseurs isolés contre les mouvements de carte parasites :
1. **Vue Satellite :** Imagerie HD actuelle (fond de référence).
2. **LIDAR HD MNT :** Cartographie altimétrique en niveaux de gris ombrés (sol nu).
3. **Sécheresse 2003 :** Missions photographiques 2000-2005 révélant les indices phytologiques et stress hydriques des structures enfouies.
4. **Photos 1950 :** État des parcelles et chemins avant le remembrement.
5. **Carte d'État-Major :** Cartographie historique du XIXe siècle.

## 4. Gestion des Sessions & Robustesse des Données
- **Verrouillage Strict :** À la fin d'une prospection (action sur STOP), les parcours et trouvailles sont gelés et archivés sous un nom personnalisé dans l'Historique.
- **Protection Anti-Écrasement :** Toute nouvelle activation du bouton PLAY engendre obligatoirement la création d'une session vierge isolée, rendant impossible la perte ou la réécriture par-dessus une archive existante.
