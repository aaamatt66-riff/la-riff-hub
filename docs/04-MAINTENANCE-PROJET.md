# Maintenance du projet La Riff Hub

## Objectif

Maintenir le Hub propre, compréhensible, sauvegardable et évolutif sans interrompre la production.

La maintenance fait partie du développement normal. Elle ne doit pas être repoussée indéfiniment ni devenir destructive.

## Principes

- La version en production reste stable pendant la préparation de la suivante.
- Toute modification doit inclure la maintenance locale des fichiers et données touchés.
- Aucun nettoyage destructif ne doit être automatisé sans inventaire et validation.
- Les anciennes versions utiles doivent être consolidées avant suppression.
- Les médias saisonniers et les anciens événements sont archivés plutôt que supprimés par défaut.
- Les données métier ne doivent être modifiées qu’à leur source de vérité.

## Domaines de maintenance

### Code

Vérifier régulièrement :
- code mort ;
- composants inutilisés ;
- dépendances inutiles ou obsolètes ;
- duplications ;
- erreurs TypeScript et avertissements ;
- compatibilité desktop, mobile, Safari et mode TV ;
- dette technique créée par les nouvelles fonctions.

### Documentation

- Lire les documents de référence avant de coder.
- Rechercher les variantes `.v2`, `.v3`, `final`, `old`, etc.
- Comparer les versions avant consolidation.
- Mettre à jour les documents impactés par chaque lot.
- Ne pas conserver plusieurs documents contradictoires comme références actives.

### GitHub

- Identifier les branches et PR encore utiles.
- Ne pas fusionner une ancienne PR uniquement parce qu’elle existe.
- Conserver l’historique des releases importantes.
- Utiliser les milestones pour regrouper les évolutions par version.
- Fermer ou reclasser les tâches devenues obsolètes.

### Vercel et hébergement

- Vérifier les déploiements, domaines et variables d’environnement.
- Contrôler les erreurs de build et de runtime.
- Ne pas supprimer une configuration avant d’avoir identifié son usage.
- Conserver une liste des éléments nécessaires pour redéployer le Hub ailleurs.

### Firebase et données

- Contrôler les collections, règles, index et fichiers de stockage.
- Ne jamais supprimer automatiquement des données métier ou médias.
- Exporter les données dans un format réutilisable lors des sauvegardes importantes.
- Documenter toute migration ou transformation de données.

### Médias

Chaque média peut avoir l’un des statuts suivants :
- actif ;
- archivé ;
- réutilisable ;
- obsolète ;
- proposé pour suppression.

Les thèmes saisonniers comme Halloween, Noël ou Saint-Patrick doivent être archivés et réutilisables d’une année à l’autre.

### Événements récurrents

Lorsqu’un événement revient :
- rechercher l’édition précédente ;
- réutiliser sa structure, ses textes et ses médias ;
- mettre à jour les dates et informations réellement modifiées ;
- conserver l’édition précédente dans l’historique.

## Fréquence

### À chaque lot

- maintenance locale du code ;
- mise à jour documentaire ;
- contrôle des impacts sur les données, médias et services externes ;
- identification des éléments à archiver ou à revoir.

### À chaque grosse release

- sauvegarde complète simple ;
- inventaire des configurations nécessaires ;
- revue des dépendances ;
- revue des branches, PR et documents ;
- archivage de la version publiée.

### Audit périodique

Un audit plus large peut être effectué quand le projet commence à accumuler plusieurs versions ou plusieurs lots importants. Il reste proportionné au projet et ne doit pas bloquer inutilement les évolutions.

## Definition of Done maintenance

Un lot ne peut pas être considéré comme terminé si :
- sa documentation n’est pas à jour ;
- il laisse volontairement des fichiers inutilisés sans justification ;
- il crée des données non sauvegardables ;
- il introduit une nouvelle source de vérité sans la documenter ;
- il rend une restauration future plus difficile sans raison.