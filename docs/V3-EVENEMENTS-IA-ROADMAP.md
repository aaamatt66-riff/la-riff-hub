# V3 - Roadmap IA des événements

Ce document complète V3-EVENEMENTS-CALENDRIER.md.

## Vision
Le Hub ne doit pas être un simple agenda mais un assistant éditorial qui détecte, enrichit, contrôle et prépare les événements avant validation humaine.

## Sources
- Calendrier Apple Brasserie (ICS/CalDAV en lecture seule)
- Hub
- GitHub
- Vercel Blob
- Firebase (si utilisé)
- Notion (optionnel)
- Sites officiels des événements

## Détection intelligente
Importer tous les événements puis les classer :
- détecté
- ignoré
- retenu
- enrichi
- à valider
- validé
- publié
- archivé

Prévoir des règles d'exclusion configurables (RDV, rendez-vous, brassage, fûtage, embouteillage, maintenance, etc.) sans supprimer les événements détectés.

## Enrichissement IA
Pour chaque événement retenu :
- rechercher les informations officielles
- récupérer horaires, lieu, description, liens, organisateur
- rechercher un visuel officiel si autorisé
- produire un score de confiance
- conserver les sources utilisées

## Multi-jours
Un événement peut couvrir plusieurs jours avec des horaires spécifiques par journée sans duplication manuelle.

## Vérifications automatiques
Détecter :
- événements oubliés
- doublons
- événements validés mais non publiés
- modifications de dates
- périodes anormalement vides

## Travail demandé à Work
- Identifier l'emplacement réel des données événements (Vercel Blob, Firebase, GitHub ou autre).
- Vérifier où sont stockés les visuels.
- Retrouver la fiche OBF existante.
- Préparer une version enrichie sans publication automatique.
- Implémenter le workflow documentaire défini dans V3-EVENEMENTS-CALENDRIER.md.
- Documenter l'architecture réellement utilisée, sans hypothèse.
