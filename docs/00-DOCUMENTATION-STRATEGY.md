# Stratégie documentaire du projet

Ce document doit être lu AVANT tout développement.

## Principe
La documentation est une partie du produit. Un développement n'est jamais terminé tant que la documentation correspondante n'est pas à jour.

## Méthode obligatoire
Pour chaque évolution :
1. Identifier les fichiers concernés.
2. Lire chaque document existant.
3. Fusionner les nouvelles informations avec les anciennes.
4. Mettre à jour les références croisées.
5. Vérifier qu'aucune information utile n'a disparu.
6. Seulement ensuite modifier le code.

## Gestion des versions documentaires
Ne jamais écraser un document important lorsqu'une refonte importante est réalisée.

Créer par exemple :
- MON-DOCUMENT.md
- MON-DOCUMENT.v2.md
- MON-DOCUMENT.v3.md

La dernière version est la référence de travail.

Avant toute modification, Work doit :
- rechercher toutes les versions disponibles ;
- analyser les différences entre elles ;
- utiliser la version la plus récente comme base ;
- vérifier qu'aucune information utile présente dans les anciennes versions n'a été perdue ;
- réintégrer les éléments encore valides.

Une ancienne version ne doit être supprimée qu'après vérification que son contenu est intégralement repris ou volontairement abandonné.

## Nettoyage
Lors d'un lot documentaire, Work doit :
- détecter les anciennes versions devenues inutiles ;
- proposer leur suppression ;
- supprimer uniquement après validation que rien n'est perdu.

## Definition of Done
Un lot est terminé uniquement si :
- le code fonctionne ;
- les tests passent ;
- les documents impactés sont mis à jour ;
- les nouvelles décisions sont documentées ;
- les anciens documents ont été vérifiés ;
- les doublons documentaires ont été traités.

## Priorité
En cas de conflit entre plusieurs documents :
1. dernière version (.v4 > .v3 > .v2 > original)
2. vérifier les versions précédentes
3. récupérer les informations encore valides
4. produire une documentation consolidée.