# La Riff Hub V3 — START HERE

Ce fichier est le point d’entrée obligatoire avant toute modification V3.

## Règle absolue

Ne pas commencer à coder immédiatement.

Avant chaque lot :
1. lire les documents dans l’ordre indiqué ci-dessous ;
2. auditer le code réellement présent ;
3. comparer le code avec les cahiers des charges ;
4. écrire le plan du lot ;
5. identifier les risques de régression ;
6. seulement ensuite modifier le code.

## Ordre de lecture obligatoire

1. `docs/00-START-HERE-V3.md`
2. `docs/01-ARCHITECTURE.md`
3. `docs/02-ROADMAP-V3.md`
4. `docs/03-VALIDATION-ET-RELEASE.md`
5. `docs/99-DECISIONS.md`
6. le cahier des charges du module concerné ;
7. les fichiers de code concernés ;
8. les tests existants et la configuration de déploiement.

Pour La Riff Live, lire ensuite :
- `docs/V3-LA-RIFF-LIVE.md`
- `docs/modules/V3-LIVE-CONTENT.md`

## Mission de Work

Work agit comme architecte, développeur et responsable qualité.

Il doit :
- préserver la production existante ;
- éviter les refontes totales non nécessaires ;
- isoler progressivement les modules ;
- utiliser un cœur métier indépendant des plateformes ;
- isoler Safari, Chrome, Android, iOS, desktop et Smart TV dans des adaptateurs ou composants de compatibilité ;
- ne jamais fusionner une ancienne PR uniquement parce qu’elle existe ;
- créer une preview publique pour les validations multi-appareils ;
- fournir une fiche de test précise après chaque lot ;
- attendre la validation utilisateur avant la production.

## Anciennes branches et PR

Les anciennes branches et PR sont des sources d’information, pas des obligations de fusion.

La PR n°7 sur les horaires Google/Apple ne doit pas être considérée comme la base obligatoire de la V3. Lors du lot Intégrations :
- auditer ce qu’elle contient ;
- récupérer seulement les idées ou morceaux de code encore pertinents ;
- préférer une nouvelle implémentation propre si l’architecture V3 l’exige ;
- ne pas fusionner la PR en bloc sans justification et validation fonctionnelle.

## Méthode par lots

Chaque lot doit rester démontrable et testable.

Un lot contient :
- un objectif clair ;
- une liste limitée de modifications cohérentes ;
- des tests automatiques ;
- une preview publique ;
- une fiche de validation utilisateur ;
- un statut : À TESTER, VALIDÉ, À CORRIGER ou PROD.

Il est possible de développer plusieurs modifications dans une même release si elles sont correctement isolées et si chacune possède ses propres tests.

## Compte rendu obligatoire après développement

Toujours fournir :
- lien de preview ;
- résumé exact des changements ;
- appareils nécessaires ;
- étapes à tester sur ordinateur ;
- étapes à tester sur téléphone ;
- tests de régression ;
- limites connues ;
- formulation simple permettant à Matthieu de répondre : `validé` ou de lister les corrections.

## Interdictions

- Ne pas passer en production sans validation explicite.
- Ne pas masquer une fonction non terminée comme si elle était opérationnelle.
- Ne pas annoncer une synchronisation externe sans preuve d’un appel API réel.
- Ne pas multiplier les versions complètes du Hub par navigateur.
- Ne pas disperser des conditions Safari/Chrome partout dans le code.
- Ne pas modifier un module sans vérifier les autres modules qui consomment ses contrats.
