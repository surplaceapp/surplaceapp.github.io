# Site public de SurPlace

Les deux pages que l'App Store exige pour l'application **SurPlace**, plus une
page de fond, hébergées par GitHub Pages. Ce dépôt est public : le code de
l'application n'y est pas et n'a pas à y être.

| Fichier | Rôle | À renseigner dans App Store Connect |
| --- | --- | --- |
| `index.html` | Aide et support | **URL de support** |
| `confidentialite.html` | Politique de confidentialité | **URL de politique de confidentialité** |
| `facturation-electronique.html` | Ce que la réforme change pour un artisan | — |

La troisième n'est exigée par personne. Elle répond à une question que les
utilisateurs se posent avant même de chercher une application, et c'est ce qui
la rend utile : une page qui explique honnêtement une réforme se fait reprendre
et citer, une page qui vend une application ne se fait pas reprendre. Elle dit
donc aussi ce que SurPlace **ne fait pas** — elle fabrique le fichier, elle ne
le dépose pas, n'étant pas une plateforme agréée.

Pages statiques, sans dépendance ni outil de construction : aucune ressource
externe, tout est en ligne dans le fichier.

## Publier : par l'interface web, et les deux historiques qui en découlent

**Cette copie locale n'a pas de remote**, et la machine ne porte aucune
authentification GitHub — ni clé SSH, ni `gh`, ni jeton. Les mises en ligne
passent donc par l'interface web : *Add file → Upload files*, en déposant les
fichiers modifiés.

Conséquence à connaître avant de brancher un remote un jour : **les deux
historiques ont divergé**. Chaque dépôt porte ses propres commits pour le même
travail — contenus identiques, identifiants différents. Le jour venu, partir de
l'état de GitHub (cloner à côté, ou `fetch` puis aligner la copie locale
dessus) ; ne pas pousser l'historique local par-dessus, il réécrirait des
commits qui existent déjà là-bas sous un autre nom.

**Ce qui déclenche la publication est un commit sur `main`**, qui lance le
workflow *pages build and deployment*. À retenir du 17 août 2026 : pendant un
incident GitHub, ce workflow a d'abord échoué (téléchargement de
`jekyll-build-pages` en 429, puis 503), et sa relance est restée **deux heures
en file d'attente sans jamais démarrer**. Ce n'est pas la relance qui a débloqué
la situation mais un **commit neuf**, qui a créé un run indépendant : la page
était en ligne une minute après. Si un déploiement paraît figé, ne pas
s'acharner sur « Re-run jobs » — committer quelque chose d'utile.

## Cohérence à tenir

La politique de confidentialité affirme qu'aucune donnée ne quitte l'appareil.
Trois choses doivent dire la même chose, faute de quoi l'examen App Store le
relève :

- cette page ;
- les **étiquettes de confidentialité** dans App Store Connect
  (« Aucune donnée collectée ») ;
- le fichier `PrivacyInfo.xcprivacy` du dépôt de l'application.

Le jour où l'application enverra quoi que ce soit sur un réseau — statistiques,
sauvegarde en ligne, compte utilisateur —, les trois sont à reprendre ensemble.

La date de dernière mise à jour est écrite en haut de `confidentialite.html` :
la corriger à chaque modification de fond.
