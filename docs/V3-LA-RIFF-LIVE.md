# La Riff Hub V3 — Module « La Riff Live »

## Objectif

Créer un moteur de jeux interactifs léger, intégré à l’univers La Riff Hub, avec la télévision comme écran collectif, les smartphones comme manettes et l’admin comme poste de pilotage.

Jeux prioritaires :
- Blind Test
- Quiz thématiques et multi-niveaux
- Battle musicale
- Vote de la salle pour choisir l’animation ou le thème suivant

Le Hub ne stocke aucun fichier audio. Apple Music sert uniquement à lire les morceaux. Les pages de jeu sont séparées du Hub principal pour rester légères et compatibles iPhone, Android, tablette et ordinateur.

## Cycle d’une partie

1. Le Game Master sélectionne un jeu et ouvre les inscriptions.
2. La TV bascule sur l’écran d’attente et affiche le QR code, le thème, le nombre d’inscrits et les pseudos/équipes qui arrivent.
3. Les joueurs rejoignent librement. Le Game Master décide seul quand les inscriptions sont closes, quel que soit le nombre de participants.
4. Le Game Master arme chaque manche. Le Hub affiche 3-2-1 puis attend le lancement manuel de la musique et du chrono.
5. Le système ouvre les réponses, ferme la manche, calcule les scores et affiche la bonne réponse et le classement.
6. Aucune manche suivante ne démarre sans validation manuelle du Game Master.
7. En fin de partie, la TV affiche podium, scores et statistiques pendant une durée réglable.
8. Un écran de clôture prend ensuite le relais avec remerciement, prochain rendez-vous, invitation à revenir et QR code du Hub.

## Pseudos temporaires puis sauvegarde facultative

### Entrée immédiate

Pour rejoindre une première partie, le joueur saisit seulement un pseudo disponible dans la session. Aucun compte, e-mail, mot de passe ou PIN n’est demandé à l’entrée.

Le pseudo temporaire n’est réservé que pour la partie en cours. Plusieurs personnes différentes peuvent donc utiliser « Matt » à des dates différentes tant qu’aucun profil permanent portant exactement ce pseudo n’a été sauvegardé.

### Sauvegarde en fin de partie

Après les résultats, le joueur peut choisir :

- `Continuer sans sauvegarder` : le pseudo et le détail personnel expirent après la durée prévue ;
- `Conserver mon pseudo et mon score` : le joueur choisit ou reçoit un PIN à quatre chiffres.

Après sauvegarde :

- le pseudo devient réservé ;
- le PIN est requis pour le reprendre lors d’une prochaine partie ;
- l’historique, les badges et les scores sont récupérés ;
- le PIN est stocké sous forme de hash et n’apparaît jamais sur la TV.

Si une personne saisit un pseudo permanent sans connaître le PIN, elle doit choisir un autre pseudo.

### Modification du pseudo

Un joueur connecté avec son pseudo et son PIN peut demander une modification. Pour éviter les abus, la V1 privilégie une validation par le Game Master :

> « Pour modifier votre pseudo, adressez-vous au Game Master. »

Le Game Master peut renommer, fusionner, désactiver ou supprimer un profil et réinitialiser son PIN.

## Joueurs et équipes

Chaque joueur peut jouer seul ou rejoindre une équipe.

- Taille maximale par défaut : 4 joueurs par équipe.
- Limite configurable par le Game Master selon le jeu.
- Une équipe peut jouer avec seulement une partie de ses membres habituels.
- Classement individuel et classement par équipe.

Pour un Blind Test en équipe, la première réponse envoyée par un membre verrouille la réponse de toute l’équipe. Les autres voient qui a répondu. Une mauvaise réponse engage donc l’équipe entière.

Les équipes peuvent elles aussi être sauvegardées par nom + PIN, mais sans QR code permanent individuel en V1 afin d’éviter une usine à gaz.

## Écran TV

Pendant les inscriptions, afficher :
- identité La Riff Live ;
- jeu et thème ;
- QR code ;
- nombre de joueurs et d’équipes ;
- pseudos ou noms d’équipes qui rejoignent ;
- état « En attente du lancement par le Game Master ».

Ne jamais afficher :
- PIN ;
- identifiants techniques ;
- réponses individuelles avant fermeture de la manche.

Le nombre de participants n’est pas limité par la capacité d’affichage de la TV. En cas de forte affluence, afficher un compteur, une liste défilante et seulement les meilleurs au classement.

## Admin / Game Master

Nouvelle rubrique : `Admin > La Riff Live`.

Fonctions :
- choisir le jeu et le contenu ;
- ouvrir et fermer les inscriptions ;
- voir les inscriptions en temps réel ;
- limiter les joueurs par équipe ;
- armer la manche ;
- lancer le 3-2-1 ;
- lancer/arrêter le chrono ;
- afficher la réponse et le classement ;
- passer manuellement à la manche suivante ;
- terminer la partie ;
- régler la durée du podium et de l’écran de clôture ;
- administrer joueurs, équipes, pseudos et PIN ;
- lancer un tirage au sort parmi les inscrits.

## Playlists Apple Music

Plusieurs volumes par thème :
- Métal
- Rock
- Riffs de guitare
- Dessins animés anciens
- Dessins animés récents
- Dessins animés intergénérationnels
- Années 1980, 1990, 2000
- Pop/Rock
- Génériques TV
- Musiques de films
- Famille/enfants

Règles :
- vérifier la disponibilité Apple Music France ;
- privilégier les intros et riffs reconnaissables ;
- garder certains groupes entre volumes mais changer de chanson ;
- éviter les ordres répétitifs ;
- permettre plusieurs variantes de chaque playlist.

Le Hub conserve uniquement les métadonnées légères : titre, artiste, ordre, réponses proposées, durée de manche et lien Apple Music facultatif.

## Quiz

Prévoir :
- thèmes bière, brassage, science, astronomie, histoire, musique, métal, Orléans, culture générale, dessins animés, cinéma, etc. ;
- niveaux enfant, facile, intermédiaire, difficile et expert ;
- possibilité de mixer les niveaux ;
- anecdote ou explication après chaque réponse.

## Résultats, partage et fidélisation

Fin de partie :
- podium équipes ;
- podium individuel ;
- score ;
- nombre de bonnes réponses ;
- meilleur temps ;
- meilleure série ;
- badges.

Chaque joueur ou équipe peut générer une carte légère de résultat aux couleurs de La Riff, avec bouton de partage via la feuille de partage native du téléphone vers Instagram, Facebook, WhatsApp ou autre application disponible.

Badges possibles : premier podium, roi du métal, maître des génériques, expert bière, éclair, dix victoires, série parfaite.

## Architecture et performance

- Next.js conservé.
- Pages publiques distinctes : `/live/blind-test`, `/live/quiz`, `/live/battle`, `/live/vote`.
- Service temps réel léger compatible Vercel : Supabase Realtime, Firebase ou équivalent.
- Heure serveur comme référence pour les réponses.
- Première réponse verrouillée côté serveur.
- Reconnexion sans perte de session.
- Aucun audio ni vidéo hébergé.
- Images rares et optimisées.
- Nettoyage automatique des données temporaires.
- Objectif V1 : 30 à 50 équipes, avec tests de charge à 10, 25, 50 et 100 connexions.

## Ordre de développement

1. Socle temps réel, QR code, salle d’attente et Game Master.
2. Pseudos temporaires et sauvegarde facultative par PIN.
3. Joueurs, équipes et double classement.
4. Blind Test.
5. Quiz multi-thèmes et multi-niveaux.
6. Battle musicale et vote de la salle.
7. Résultats partageables, badges, tirage au sort et Hall of Fame.
