# Site public de SurPlace

Les deux pages que l'App Store exige pour l'application **SurPlace**, hébergées
par GitHub Pages. Rien d'autre : ce dépôt est public, le code de l'application
n'y est pas et n'a pas à y être.

| Fichier | Rôle | À renseigner dans App Store Connect |
| --- | --- | --- |
| `index.html` | Aide et support | **URL de support** |
| `confidentialite.html` | Politique de confidentialité | **URL de politique de confidentialité** |

Pages statiques, sans dépendance ni outil de construction : aucune ressource
externe, tout est en ligne dans le fichier. On modifie le HTML, on pousse, la
page est à jour en une minute.

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
