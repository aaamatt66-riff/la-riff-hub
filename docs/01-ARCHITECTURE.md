# La Riff Hub — Architecture globale

## 1. Principe directeur

Le Hub doit être conçu comme un ensemble de modules indépendants reposant sur un cœur commun, et non comme une seule application monolithique où chaque modification risque d'en casser une autre.

L'idée directrice est comparable à une architecture en couches :

- le cœur métier contient les règles fonctionnelles ;
- les interfaces utilisateur consomment ce cœur ;
- les spécificités de plateforme sont isolées dans des adaptateurs ;
- les services externes sont branchés derrière des contrats stables ;
- un changement de navigateur, de téléphone, de TV, de base ou d'API ne doit pas obliger à réécrire le cœur métier.

## 2. Architecture cible

```text
La Riff Hub

├── Core métier
│   ├── modèles de données
│   ├── règles métier
│   ├── permissions
│   ├── événements internes
│   └── contrats de services
│
├── Modules fonctionnels
│   ├── Carte / produits
│   ├── Événements
│   ├── Actualités
│   ├── Horaires
│   ├── TV
│   ├── Statistiques
│   ├── Thèmes
│   ├── La Riff Live
│   ├── Consigne
│   └── Synchronisations externes
│
├── Interfaces
│   ├── Hub public
│   ├── Admin principal
│   ├── Admin TV
│   ├── Admin La Riff Live / Game Master
│   ├── Écran TV
│   └── Pages mobiles de jeu
│
├── Adaptateurs de plateforme
│   ├── Safari iOS
│   ├── Chrome Android
│   ├── navigateurs desktop
│   ├── Smart TV
│   └── PWA
│
└── Adaptateurs de services
    ├── base de données
    ├── temps réel
    ├── stockage d'images
    ├── Apple Music
    ├── Google Business Profile
    ├── Apple Business Connect
    └── calendriers
```

## 3. Cœur métier indépendant

Le cœur métier ne doit jamais dépendre directement :

- de Safari ;
- de Chrome ;
- d'iOS ;
- d'Android ;
- d'une Smart TV particulière ;
- de Firebase, Supabase ou d'une base précise ;
- d'Apple Music ;
- d'une API Google ou Apple.

Le cœur métier expose uniquement des fonctions et contrats stables.

Exemples :

- `createGameSession()`
- `registerPlayer()`
- `submitAnswer()`
- `calculateScore()`
- `publishEvent()`
- `getOpeningStatus()`
- `renderTvPlaylist()`

Les plateformes et services externes traduisent ensuite ces opérations dans leur propre langage technique.

## 4. Adaptateurs de plateforme

Les différences de navigateur ou d'appareil doivent être isolées.

Exemples de responsabilités :

### Safari iOS

- gestion du plein écran limité ;
- particularités de la PWA ;
- feuille de partage Apple ;
- comportement audio ou veille écran ;
- safe areas et barres système.

### Chrome Android

- installation PWA ;
- feuille de partage Android ;
- comportement plein écran ;
- notifications ou badges si autorisés plus tard.

### Smart TV

- navigation sans souris ;
- tailles d'écran variables ;
- performances plus faibles ;
- absence possible de certaines API modernes ;
- maintien de l'écran éveillé.

### Desktop

- administration ;
- prévisualisation ;
- saisie de contenu ;
- tests multi-fenêtres.

Une correction spécifique à Safari doit être placée dans la couche Safari ou dans un composant de compatibilité, pas dispersée dans tout le code.

## 5. Détection par capacité, pas seulement par marque

Le code ne doit pas se limiter à demander : « Est-ce un iPhone ? » ou « Est-ce Chrome ? ».

Il doit d'abord vérifier les capacités disponibles :

- partage natif disponible ;
- plein écran disponible ;
- stockage local disponible ;
- WebSocket disponible ;
- affichage installé en PWA ;
- écran tactile ;
- mode paysage ;
- réduction des animations demandée.

Cette approche rend le Hub compatible avec de futurs appareils ou navigateurs sans devoir les connaître à l'avance.

## 6. Contrats stables entre modules

Chaque module publie une interface claire.

Exemple : le module Événements peut fournir :

- `listUpcomingEvents()`
- `getNextEvent()`
- `subscribeToEventChanges()`

Le module TV utilise ces fonctions mais ne lit pas directement les tables internes du module Événements.

Ainsi, le stockage ou la structure interne des événements peut changer sans casser la TV.

## 7. Bus d'événements interne

Les modules communiquent autant que possible par événements métier plutôt que par dépendances directes.

Exemples :

- `EVENT_PUBLISHED`
- `OPENING_HOURS_UPDATED`
- `TV_THEME_CHANGED`
- `GAME_SESSION_STARTED`
- `PLAYER_JOINED`
- `ROUND_COMPLETED`

Le module concerné publie l'événement. Les autres modules intéressés réagissent sans connaître son implémentation interne.

## 8. Administrations par familles

L'administration ne doit plus être une seule longue page contenant tout.

Architecture recommandée :

### Accueil Admin

Tableau de bord avec familles :

- Contenus
- Exploitation
- TV
- La Riff Live
- Statistiques
- Apparence et thèmes
- Intégrations
- Paramètres techniques

Chaque famille ouvre son propre espace, avec sa navigation et ses droits éventuels.

Le même système d'authentification admin est conservé, mais chaque espace ne charge que ses composants et données.

Avantages :

- interface plus lisible ;
- chargement plus léger ;
- réduction des effets de bord ;
- tests plus ciblés ;
- possibilité de faire évoluer une administration sans toucher aux autres.

## 9. Organisation du code recommandée

```text
src/
├── core/
│   ├── domain/
│   ├── contracts/
│   ├── events/
│   └── permissions/
├── modules/
│   ├── menu/
│   ├── events/
│   ├── news/
│   ├── opening-hours/
│   ├── tv/
│   ├── stats/
│   ├── themes/
│   └── live/
├── interfaces/
│   ├── public-hub/
│   ├── admin/
│   ├── tv/
│   └── live-player/
├── adapters/
│   ├── platforms/
│   │   ├── safari-ios/
│   │   ├── chrome-android/
│   │   ├── desktop/
│   │   └── smart-tv/
│   └── services/
│       ├── database/
│       ├── realtime/
│       ├── storage/
│       ├── apple-music/
│       ├── google-business/
│       └── apple-business/
└── shared/
    ├── ui/
    ├── validation/
    ├── logging/
    └── testing/
```

Cette structure est une cible. La migration depuis le code existant doit être progressive, jamais une réécriture brutale de tout le Hub.

## 10. Règles de compatibilité

Chaque fonctionnalité doit définir :

- navigateurs supportés ;
- appareils supportés ;
- capacités requises ;
- solution de repli ;
- tests obligatoires.

Matrice minimale :

- Safari iPhone récent ;
- Chrome Android récent ;
- Safari macOS ;
- Chrome desktop ;
- écran TV actuel ;
- PWA installée ;
- navigation web non installée.

## 11. Corrections spécifiques sans régression

Lorsqu'un bug ne concerne qu'une plateforme :

1. reproduire et documenter la plateforme concernée ;
2. identifier si le problème vient du cœur ou de l'adaptateur ;
3. corriger au niveau le plus local possible ;
4. ajouter un test de non-régression spécifique ;
5. vérifier les autres plateformes avec les tests existants ;
6. ne pas créer de branche parallèle complète du produit par plateforme.

Il ne faut pas développer un Hub iPhone et un Hub Android séparés. Il faut conserver un seul cœur et de petites adaptations locales.

## 12. Règle de migration

Avant tout gros ajout V3 :

- cartographier le code actuel ;
- identifier les dépendances croisées ;
- extraire les contrats communs ;
- isoler progressivement les modules ;
- ajouter les tests avant les refontes risquées ;
- préserver la production existante pendant toute la migration.

## 13. Critères d'acceptation architecturaux

Une fonctionnalité n'est pas considérée terminée si :

- elle lit directement les données privées d'un autre module sans contrat ;
- elle contient des conditions navigateur dispersées partout ;
- elle oblige à charger une administration complète pour une seule action ;
- elle ne possède pas de solution de repli ;
- elle n'est testable qu'en production ;
- elle mélange logique métier, affichage et accès aux services externes dans le même composant.

## 14. Principe final

Un changement de plateforme, de navigateur, de base de données ou de service externe doit remplacer un adaptateur, pas remettre en cause tout le Hub.
