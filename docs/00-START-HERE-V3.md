# La Riff Hub V3 — START HERE

Ce fichier est le point d’entrée obligatoire avant toute modification V3.

## Règle absolue

Ne pas commencer à coder immédiatement.

Avant chaque lot :
1. lire les documents dans l’ordre indiqué ci-dessous ;
2. rechercher les éventuelles versions plus récentes d’un même document (`.v2`, `.v3`, etc.) ;
3. comparer les versions disponibles et récupérer les informations encore valides ;
4. auditer le code réellement présent ;
5. comparer le code avec les cahiers des charges ;
6. écrire le plan du lot ;
7. identifier les risques de régression ;
8. identifier les impacts sur GitHub, Vercel, Firebase, les données et les médias ;
9. seulement ensuite modifier le code.

La méthode documentaire obligatoire est : **Lecture → Fusion → Mise à jour**.

## Ordre de lecture obligatoire

1. `docs/00-START-HERE-V3.md`
2. `docs/00-DOCUMENTATION-STRATEGY.md`
3. `docs/01-VERSIONING-RELEASES-MILESTONES.md`
4. `docs/04-MAINTENANCE-PROJET.md`
5. `docs/01-ARCHITECTURE.md`
6. `docs/02-ROADMAP-V3.md`
7. `docs/03-VALIDATION-ET-RELEASE.md` si présent
8. `docs/99-DECISIONS.md`
9. le cahier des charges du module concerné ;
10. les fichiers de code concernés ;
11. les tests existants et la configuration de déploiement.

Si un document annoncé n’existe pas, Work doit le signaler et vérifier s’il existe sous un autre nom avant d’en créer un nouveau.

Pour La Riff Live, lire ensuite :
- `docs/V3-LA-RIFF-LIVE.md`
- `docs/modules/V3-LIVE-CONTENT.md`

## Mission de Work

Work agit comme architecte, développeur, responsable qualité et responsable de maintenance.

Il doit :
- préserver la production existante ;
- éviter les refontes totales non nécessaires ;
- isoler progressivement les modules ;
- utiliser un cœur métier indépendant des plateformes ;
- isoler Safari, Chrome, Android, iOS, desktop et Smart TV dans des adaptateurs ou composants de compatibilité ;
- ne jamais fusionner une ancienne PR uniquement parce qu’elle existe ;
- créer une preview publique pour les validations multi-appareils ;
- fournir une fiche de test précise après chaque lot ;
- mettre à jour la documentation impactée ;
- effectuer le nettoyage local du code, des fichiers et des données touchés ;
- vérifier les impacts sur Vercel, Firebase et les autres services ;
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
- une milestone ou une version cible identifiée ;
- des tests automatiques ;
- une preview publique ;
- une fiche de validation utilisateur ;
- une revue documentaire ;
- une revue de maintenance locale ;
- un statut : À TESTER, VALIDÉ, À CORRIGER ou PROD.

Il est possible de développer plusieurs modifications dans une même release si elles sont correctement isolées et si chacune possède ses propres tests.

La version stable reste en production. La version suivante (`V3.1`, `V3.2`, etc.) est développée et testée séparément, puis mise en production uniquement après validation explicite.

## Definition of Done

Un lot n’est terminé que si :
- le code fonctionne ;
- le build et les tests passent ;
- les régressions ont été vérifiées ;
- la documentation impactée a été mise à jour ;
- les anciennes versions documentaires ont été comparées si elles existent ;
- le nettoyage local a été effectué ;
- les intégrations et services externes concernés ont été contrôlés ;
- une procédure de retour arrière est possible ;
- Matthieu a validé la mise en production.

## Compte rendu obligatoire après développement

Toujours fournir :
- version ou milestone concernée ;
- lien de preview ;
- résumé exact des changements ;
- fichiers et documents modifiés ;
- appareils nécessaires ;
- étapes à tester sur ordinateur ;
- étapes à tester sur téléphone ;
- tests de régression ;
- impacts Vercel, Firebase, données et médias ;
- nettoyage effectué ou proposé ;
- limites connues ;
- formulation simple permettant à Matthieu de répondre : `validé` ou de lister les corrections.

## Interdictions

- Ne pas passer en production sans validation explicite.
- Ne pas masquer une fonction non terminée comme si elle était opérationnelle.
- Ne pas annoncer une synchronisation externe sans preuve d’un appel API réel.
- Ne pas multiplier les versions complètes du Hub par navigateur.
- Ne pas disperser des conditions Safari/Chrome partout dans le code.
- Ne pas modifier un module sans vérifier les autres modules qui consomment ses contrats.
- Ne pas supprimer automatiquement un média saisonnier ou un événement récurrent.
- Ne pas effectuer de nettoyage destructif sur GitHub, Vercel, Firebase ou les données sans inventaire et validation.