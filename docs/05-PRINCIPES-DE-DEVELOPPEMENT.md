# La Riff Hub V3 — Principes de développement

Ce document définit les règles obligatoires de qualité du code pour toute la V3 et les évolutions futures.

## 1. Objectif

Le Hub doit rester :

- propre ;
- léger ;
- rapide ;
- lisible ;
- testable ;
- maintenable ;
- sans vestiges inutiles.

Le fait qu'un ancien code « fonctionne encore » ne suffit pas à justifier sa conservation.

## 2. Zéro code mort

À chaque lot, supprimer systématiquement :

- fonctions jamais appelées ;
- composants jamais utilisés ;
- variables inutiles ;
- imports inutilisés ;
- anciennes routes abandonnées ;
- anciens fichiers de test devenus faux ;
- anciens styles CSS non utilisés ;
- images et ressources non référencées ;
- options de configuration obsolètes ;
- commentaires décrivant un ancien fonctionnement ;
- anciens contournements devenus inutiles ;
- dépendances npm non utilisées.

Aucun fichier ne doit être conservé « au cas où » dans le code de production. L'historique Git sert précisément à retrouver une ancienne version si nécessaire.

## 3. Nettoyage obligatoire à chaque modification

Lorsqu'un fichier est modifié, Work doit aussi vérifier :

- si des lignes sont devenues inutiles ;
- si la logique peut être simplifiée ;
- si un doublon peut être supprimé ;
- si les noms restent clairs ;
- si les commentaires sont encore exacts ;
- si les imports peuvent être réduits ;
- si les types sont corrects ;
- si le fichier devient trop gros et doit être découpé.

La règle est : laisser chaque zone plus propre qu'avant l'intervention.

## 4. Pas de duplication

Toute logique répétée doit être analysée.

Si deux modules font réellement la même chose :

- extraire une fonction commune ;
- créer un composant partagé ;
- créer un contrat commun ;
- ou documenter pourquoi la duplication est volontaire.

Il ne faut pas créer une abstraction artificielle pour deux comportements qui ne sont qu'en apparence similaires.

## 5. Fichiers courts et responsabilités claires

Un fichier doit avoir une responsabilité principale.

Éviter :

- composants géants ;
- pages contenant métier, accès aux données, affichage et compatibilité navigateur ;
- fonctions aux effets multiples ;
- fichiers « utils » fourre-tout ;
- constantes dispersées.

Découper lorsqu'un fichier devient difficile à comprendre, tester ou modifier sans risque.

## 6. Dépendances minimales

Avant d'ajouter une dépendance externe :

1. vérifier si le besoin peut être couvert proprement sans elle ;
2. vérifier sa maintenance ;
3. vérifier son poids ;
4. vérifier son impact navigateur ;
5. vérifier sa licence ;
6. documenter la raison de son ajout.

Supprimer toute dépendance devenue inutile.

## 7. Performance et poids

Chaque lot doit vérifier :

- taille des bundles ;
- chargement différé des modules lourds ;
- images optimisées ;
- absence de requêtes inutiles ;
- absence de re-rendus excessifs ;
- absence d'écouteurs ou abonnements non nettoyés ;
- absence de données chargées sans être affichées ;
- cache approprié ;
- code spécifique à l'admin non chargé sur le Hub public ;
- code spécifique à La Riff Live non chargé hors des pages Live.

La priorité est la vitesse réelle sur téléphone et Smart TV, pas seulement les performances sur un ordinateur récent.

## 8. Nettoyage des données et services

Ne pas limiter le nettoyage au code.

Vérifier également :

- anciennes tables ou colonnes inutilisées ;
- anciennes variables d'environnement ;
- anciens endpoints ;
- anciens webhooks ;
- anciennes règles de sécurité ;
- anciens fichiers de stockage ;
- anciennes tâches automatiques ;
- anciennes fonctions serveur.

Toute suppression de données doit être précédée d'une vérification et, si nécessaire, d'une sauvegarde.

## 9. Outils de contrôle

Le projet doit utiliser autant que possible :

- TypeScript strict ;
- ESLint ;
- formatage automatique ;
- détection des imports inutilisés ;
- détection des dépendances inutilisées ;
- tests unitaires ;
- tests d'intégration ;
- tests de bout en bout sur les parcours critiques ;
- analyse du bundle ;
- contrôle des erreurs de build ;
- vérification des logs et avertissements navigateur.

Aucun avertissement ne doit être ignoré sans justification documentée.

## 10. Critères de fin de lot

Un lot n'est pas terminé tant que :

- le build ne passe pas ;
- les tests concernés ne passent pas ;
- les imports inutilisés ne sont pas supprimés ;
- les fichiers abandonnés ne sont pas supprimés ;
- les dépendances devenues inutiles ne sont pas supprimées ;
- les logs temporaires ne sont pas retirés ;
- les commentaires temporaires ne sont pas retirés ;
- les TODO non traités ne sont pas soit résolus, soit consignés dans `04-TECHNICAL-DEBT.md` ;
- l'impact sur le poids et les performances n'est pas vérifié ;
- les régressions principales ne sont pas testées.

## 11. Audit de nettoyage V3

Le premier lot V3 doit produire un inventaire :

- code mort probable ;
- dépendances inutilisées ;
- composants trop volumineux ;
- duplications ;
- routes obsolètes ;
- styles orphelins ;
- fichiers médias inutilisés ;
- anciennes branches ou PR uniquement informatives ;
- dette technique prioritaire.

Les suppressions risquées doivent être faites progressivement avec tests et preview.

## 12. Règle finale

Le dépôt Git conserve l'histoire. Le code de production ne doit conserver que ce qui sert réellement au produit actuel ou à une évolution explicitement planifiée et documentée.
