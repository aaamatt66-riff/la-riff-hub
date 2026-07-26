# Versioning, releases et milestones

Ce document définit la manière de gérer les versions du Hub, leur archivage, leur validation et leur mise en production.

## Principe général

La version actuellement en production reste stable.

Les évolutions sont préparées dans une version suivante, par exemple :

- V3.0 : version majeure actuellement en production ;
- V3.1 : prochaine évolution en cours ;
- V3.2 : évolution suivante si V3.1 est déjà réservée ou en validation ;
- V4.0 : prochaine refonte majeure.

Une version en cours de travail ne remplace jamais la production avant validation complète.

## Numérotation

- changement majeur de structure, d'architecture ou de fonctionnalités : V4.0 ;
- ajout fonctionnel important mais compatible avec la version actuelle : V3.1, V3.2, etc. ;
- correction mineure ou technique sans changement fonctionnel majeur : V3.1.1, V3.1.2, etc.

## Cycle d'une version

1. Planifiée
2. En développement
3. En test
4. En validation manuelle
5. Validée
6. Mise en production
7. Archivée comme version livrée

Aucune étape de validation ou de mise en production n'est automatique sans contrôle explicite.

## Règle de production

- la version stable reste en production ;
- la version suivante est développée séparément ;
- elle est testée sans perturber la production ;
- elle est mise en production uniquement après validation ;
- l'ancienne version reste identifiable dans l'historique Git.

## Archivage des versions précédentes

Work doit reconstituer et documenter l'historique disponible à partir de :

- commits ;
- branches ;
- anciennes PR ;
- fichiers de documentation ;
- déploiements Vercel ;
- notes de versions ;
- éléments encore présents dans Firebase ou d'autres services.

L'historique doit être organisé par version et par pertinence.

Exemple de structure :

- V1.x : première base fonctionnelle ;
- V2.0 : première évolution majeure ;
- V2.3 : évolution intermédiaire ;
- V2.4 : évolution intermédiaire ;
- V3.0 : grande évolution fonctionnelle actuelle.

Ne pas inventer les contenus historiques lorsqu'ils ne sont pas vérifiables. Les versions anciennes doivent être qualifiées comme reconstituées si les preuves sont incomplètes.

## Milestones GitHub

Une milestone représente une version à livrer.

Exemples :

- V3.0
- V3.1
- V3.2
- V4.0

Chaque issue ou PR doit être rattachée à la milestone correspondant à la version dans laquelle elle doit être livrée.

La milestone permet de suivre :

- les fonctionnalités prévues ;
- les corrections ;
- la documentation ;
- la maintenance ;
- les tâches encore ouvertes ;
- le pourcentage d'avancement.

## Contenu minimal d'une milestone

Chaque milestone doit contenir :

- objectif de la version ;
- fonctionnalités incluses ;
- bugs à corriger ;
- documentation à mettre à jour ;
- maintenance et nettoyage prévus ;
- critères de validation ;
- statut de mise en production.

## Branches recommandées

- production : branche stable actuelle ;
- version suivante : branche dédiée, par exemple `v3.1` ;
- correctif ponctuel : branche dédiée, par exemple `fix/...` ;
- fonctionnalité : branche dédiée, par exemple `feature/...`.

Avant toute modification, Work doit vérifier la structure réelle des branches existantes et ne pas créer de nouvelle convention incompatible avec le dépôt.

## Validation avant production

Une version peut être mise en production uniquement si :

- build réussi ;
- tests réussis ;
- validation fonctionnelle effectuée ;
- contrôle mobile, desktop et TV effectué si concerné ;
- documentation mise à jour ;
- maintenance locale réalisée ;
- données et migrations vérifiées ;
- intégrations externes vérifiées ;
- retour arrière possible.

## Vercel, Firebase et autres outils

Pour chaque version, Work doit vérifier les éléments externes au code :

- déploiements Vercel ;
- variables d'environnement ;
- domaines ;
- stockage et médias ;
- Firebase, Firestore, Storage et règles de sécurité ;
- services externes réellement utilisés ;
- données obsolètes ou de test ;
- cohérence entre production et préproduction.

Aucun nettoyage destructif ne doit être effectué sans inventaire, analyse et validation.

## Médias et événements réutilisables

Les médias saisonniers, thèmes et événements récurrents ne doivent pas être supprimés automatiquement.

Ils peuvent être :

- actifs ;
- archivés ;
- réutilisables ;
- obsolètes ;
- proposés à la suppression.

Lorsqu'un événement revient, par exemple OBF 2027 après OBF 2026, Work doit :

- rechercher l'édition précédente ;
- reprendre les données encore valides ;
- mettre à jour les dates ;
- remplacer les médias uniquement si nécessaire ;
- conserver l'historique de l'ancienne édition ;
- éviter de tout recréer inutilement.

## Règle de clôture

Une version n'est clôturée que lorsque :

- elle est validée ;
- elle est en production ;
- sa documentation est consolidée ;
- sa milestone est terminée ;
- les éléments reportés sont déplacés vers la version suivante ;
- un résumé de version est conservé.