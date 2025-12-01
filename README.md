# Générateur Automatique de Messages IT

Application web statique pour générer rapidement 4 messages standardisés à partir d’un formulaire unique. Interface premium noir/vert, responsive, avec bascule Sombre/Jour, copie intuitive et historique local.

## Fonctionnalités
- Sélecteur de matériel intelligent (PC, iPhone, Imprimante, Clavier, Souris, Chargeur, Casque, Écouteurs)
- Affichage dynamique des champs requis selon le matériel (SN ancien/nouveau si requis, RITM, SCTASK, dates)
- 4 messages générés et éditables, chacun avec icône, titre, description, bouton Copier
- Copie par message et copie globale, badge “Copié ✓”, fallback robuste
- Historique des 10 dernières saisies (localStorage) et réutilisation des données
- Thème Noir/Vert sombre avec glow discret + bascule Mode Sombre/Jour
- Accessibilité: roles ARIA, labels et feedback de statut

## Les 4 messages
- A Fermeture Ticket (Tech): message court de clôture (OSS Laennec) avec date et ticket
- B Message Utilisateur: détail remplacement (nom, matériel, SN ancien/nouveau si requis, asset, SIM)
- C Mise à jour Asset (stock/WFM): état, substat, stockroom, commentaire, RITM, SCTASK
- D Excel (Othman): bloc prêt à coller (todayDate, SCTASK, RITM, SN nouveau, SN ancien)

## Logique par matériel
- SN requis: PC, iPhone, Imprimante → affichage et obligation de `SN ancien` et `SN nouveau`
- SN non requis: Clavier, Souris, Chargeur, Casque, Écouteurs → sections SN masquées
- RITM et SCTASK: toujours requis

## Utilisation
- Ouvrir `index.html` dans un navigateur moderne
- Choisir le matériel et renseigner Nom, RITM, SCTASK, Dates; SN ancien/nouveau s’affichent automatiquement si requis
- Les messages se mettent à jour en direct
- Cliquer “Copier message …” pour copier uniquement le corps du message, ou “Copier tous les messages” pour concaténer les 4 corps
- Utiliser l’historique pour recharger rapidement des données précédentes
- Bascule de thème via le bouton “Mode: Sombre/Jour” (préférence mémorisée)

## Structure du projet
- `index.html` — structure de la page et cartes de messages
- `assets/css/theme.css` — thème noir/vert + mode jour
- `assets/js/materielConfig.js` — table de décision des matériels
- `assets/js/generator.js` — moteur de templates, copie, sanitation
- `assets/js/formLogic.js` — champs dynamiques, mises à jour en direct, historique, bascule de thème

## Déploiement
- Projet statique: hébergeable sur GitHub Pages ou tout serveur statique (copie du dossier).

## Notes
- Le bouton “Copier” utilise `navigator.clipboard` avec fallback pour compatibilité.
- Les champs non requis sont masqués avec animation fade-in/out.
