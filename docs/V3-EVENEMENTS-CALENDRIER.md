# La Riff Hub V3 — Événements et calendrier éditorial

## 1. Objectif

Créer dans l'administration du Hub un calendrier mensuel clair permettant de :

- visualiser les événements du Hub ;
- visualiser les événements importés depuis le calendrier Brasserie ;
- distinguer immédiatement leur état ;
- exclure les rendez-vous internes et opérations de production ;
- enrichir automatiquement les événements publics ;
- imposer une validation humaine avant publication ;
- gérer proprement les événements sur plusieurs jours.

Le Hub reste la référence éditoriale publique. Le calendrier externe sert de source de détection et de préparation.

## 2. Vue calendrier mensuelle

L'administration doit proposer une vraie vue calendrier :

- affichage mois par mois ;
- navigation mois précédent / mois suivant ;
- retour rapide au mois courant ;
- affichage lisible sur ordinateur et mobile ;
- clic sur un événement pour ouvrir sa fiche ;
- filtres par état, source, type et visibilité ;
- légende des couleurs toujours visible ;
- possibilité de basculer en vue liste si nécessaire.

## 3. Sources d'événements

Sources possibles :

- calendrier Apple « Brasserie » via flux compatible ICS ou CalDAV ;
- calendrier Notion, uniquement si une intégration fiable est disponible ;
- saisie manuelle dans le Hub ;
- événement déjà présent dans le Hub ;
- import ponctuel ;
- détection depuis une source publique officielle.

Notion reste optionnel. Il ne doit pas devenir une dépendance obligatoire du fonctionnement principal.

## 4. Filtrage du calendrier Brasserie

Le calendrier Brasserie contient aussi des rendez-vous internes et des opérations de production.

Le système doit permettre :

- règles d'exclusion automatiques par mots-clés ;
- exclusions configurables depuis une interface simple ;
- possibilité d'ignorer une occurrence précise ;
- possibilité d'ignorer définitivement une série ;
- affichage des événements exclus dans un journal de contrôle facultatif.

Exclusions initiales proposées :

- fûtage ;
- enfûtage ;
- embouteillage ;
- brassage ;
- conditionnement ;
- livraison interne ;
- rendez-vous fournisseur ;
- maintenance ;
- nettoyage ;
- production.

Une exclusion automatique ne supprime jamais l'événement source. Elle empêche seulement sa proposition comme événement public.

## 5. États éditoriaux obligatoires

Chaque événement suit une machine à états stricte.

### 5.1 Détecté

Événement trouvé dans une source externe mais pas encore sélectionné pour publication.

Affichage recommandé : gris.

### 5.2 Retenu

Matthieu indique que l'événement doit potentiellement apparaître publiquement.

Aucune publication n'est encore possible.

### 5.3 En cours d'enrichissement

L'assistant recherche et prépare :

- titre public ;
- description ;
- horaires ;
- lieu ;
- organisateur ;
- liens officiels ;
- visuel autorisé ;
- informations pratiques ;
- sources utilisées.

### 5.4 À valider

La fiche est suffisamment complète pour être relue.

Elle doit présenter clairement :

- les informations importées ;
- les informations ajoutées ou corrigées ;
- les sources ;
- les éventuelles incertitudes ;
- un aperçu du rendu Hub et TV.

### 5.5 Validé

Matthieu confirme explicitement le contenu et les canaux de diffusion.

Un événement validé n'est pas nécessairement encore publié.

### 5.6 Publié

L'événement est effectivement présent sur les canaux sélectionnés.

Le statut Publié ne peut être attribué qu'après vérification technique de la publication réelle.

### 5.7 Terminé, annulé ou archivé

États de fin de vie distincts.

Un événement annulé doit pouvoir afficher une information d'annulation avant archivage.

## 6. Garde-fous de publication

Règles obligatoires :

- aucune publication sans validation explicite ;
- aucune validation si les champs obligatoires manquent ;
- aucun statut Publié si les données n'ont pas réellement été enregistrées et exposées ;
- aucun statut Validé déduit automatiquement ;
- historique des changements conservé ;
- possibilité de revenir à une version précédente ;
- source et date de vérification visibles dans l'administration ;
- aperçu obligatoire avant publication ;
- détection des doublons avant création.

## 7. Événements sur plusieurs jours

Le modèle de données doit gérer nativement un événement couvrant plusieurs jours.

Un événement parent contient :

- titre ;
- description ;
- lieu principal ;
- organisateur ;
- visuel ;
- liens ;
- date de début ;
- date de fin ;
- état éditorial ;
- sources.

Chaque journée possède sa propre occurrence avec :

- date ;
- heure d'ouverture ;
- heure de fermeture ;
- horaires spécifiques ;
- lieu spécifique éventuel ;
- note spécifique ;
- statut spécifique si nécessaire.

Exemple : Salon de la gastronomie du 28 au 31 octobre.

L'administrateur crée une seule fiche parent puis renseigne les horaires jour par jour. Le Hub génère les occurrences sans obliger à dupliquer manuellement quatre fiches.

## 8. Affichage public d'un événement multi-jours

Selon le contexte, le Hub peut afficher :

- une seule fiche avec toutes les dates et horaires ;
- une occurrence par jour dans le calendrier ;
- une seule carte condensée sur la page événements ;
- les horaires du jour courant mis en avant ;
- une mention « du ... au ... » ;
- les journées passées atténuées sans supprimer l'événement complet.

Le mode TV doit éviter les duplications visuelles inutiles tout en indiquant clairement les jours et horaires.

## 9. Enrichissement automatique

Pour un événement retenu, l'assistant peut rechercher les compléments sur le web, en privilégiant :

1. site officiel de l'événement ;
2. site officiel de l'organisateur ;
3. réseaux sociaux officiels ;
4. programme officiel ;
5. sources institutionnelles ;
6. médias locaux fiables.

Chaque information ajoutée doit conserver :

- URL ou référence source ;
- date de consultation ;
- niveau de confiance ;
- indication claire en cas d'inférence.

Les visuels ne doivent être utilisés que si leur usage est autorisé ou s'ils sont fournis par l'organisateur.

## 10. Détection des oublis

Le système doit comparer :

- calendrier Brasserie ;
- événements Hub ;
- événements publiés ;
- événements récurrents attendus ;
- événements publics détectés.

Alertes possibles :

- événement du calendrier absent du Hub ;
- événement Hub sans horaires complets ;
- événement retenu jamais enrichi ;
- événement validé mais non publié ;
- événement publié mais non implémenté sur un canal demandé ;
- doublon probable ;
- changement de date ou d'horaire détecté ;
- afterwork attendu mais absent ;
- période anormalement vide.

## 11. Interface simple

L'administration ne doit pas devenir une usine à gaz.

Écran principal :

- calendrier mensuel ;
- couleurs par état ;
- filtres simples ;
- panneau latéral ou fenêtre de détail ;
- boutons d'action adaptés à l'état courant ;
- un bouton principal évident par étape.

Exemple de parcours :

1. événement gris détecté ;
2. clic « Retenir » ;
3. enrichissement préparé ;
4. clic « Vérifier » ;
5. aperçu ;
6. clic « Valider » ;
7. clic « Publier » ;
8. confirmation technique du statut Publié.

Les réglages avancés restent dans une section secondaire.

## 12. Synchronisation Apple

Approche privilégiée : lire uniquement le calendrier Apple « Brasserie ».

Solutions à évaluer :

- abonnement ICS en lecture seule ;
- accès CalDAV sécurisé ;
- synchronisation intermédiaire vers un calendrier compatible ;
- automatisation Apple locale si nécessaire.

La solution retenue doit :

- éviter l'accès aux autres calendriers personnels ;
- fonctionner en lecture seule par défaut ;
- gérer les événements modifiés ou supprimés ;
- ne jamais publier automatiquement ;
- documenter clairement les limites techniques.

## 13. Rôle éventuel de Notion

Notion peut servir :

- de source complémentaire ;
- de tableau éditorial ;
- de banque de contenus ;
- d'espace de préparation collaborative.

Il ne doit pas être nécessaire pour consulter, valider ou publier les événements dans le Hub.

## 14. Critères de validation du module

Le module n'est pas terminé tant que :

- la vue mensuelle fonctionne ;
- la navigation entre mois fonctionne ;
- les événements importés sont visuellement distincts ;
- les exclusions par mots-clés fonctionnent ;
- un événement multi-jours avec horaires différents est correctement géré ;
- le workflow interdit une publication sans validation ;
- le statut Publié correspond à une publication réelle ;
- les sources sont consultables ;
- les doublons sont détectés ;
- les tests de régression passent ;
- l'interface reste compréhensible sans formation.
