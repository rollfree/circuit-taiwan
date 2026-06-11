---
title: "Protocole Médical et Architecture de Sécurité Terrain"
description: "Télémétrie en temps réel, alertes fonctionnant hors ligne et protocoles de réponse vérifiés pour une circumnavigation de Taïwan de 35 jours."
summary: "Circuit Taiwan déploie un système de sécurité multi-couches : surveillance continue des signes vitaux, détection de foudre (AS3935), intégration d'API météo et points d'extraction pré-cartographiés. Tous les protocoles sont testés sur le terrain et supervisés médicalement."
date: 2026-06-03
draft: false
tags: ["medical", "safety", "engineering", "telemetry"]
toc: true
---

Circuit Taiwan n'est pas seulement une expédition—c'est une **étude médicale mobile sur le terrain**. Sur 35 jours, nous collecterons des données physiologiques et environnementales continues tout en maintenant des protocoles de sécurité supervisés médicalement à chaque kilomètre.

Ce document présente l'architecture de sécurité opérationnelle, les seuils d'alerte et les protocoles de réponse qui protègent le leader d'expédition tout au long du voyage.

<!--more-->

## Architecture de Surveillance Continue

### Télémétrie des Signes Vitaux (Temps Réel)

| Paramètre | Capteur | Fréquence d'Échantillonnage | Seuil d'Alerte | Seuil Critique |
|-----------|---------|----------------------------|----------------|----------------|
| **Fréquence Cardiaque** | Ceinture thoracique Polar H10 | 1 Hz (chaque seconde) | <45 ou >160 bpm | <35 ou >180 bpm |
| **SpO₂ (Saturation Oxygène)** | Oxymètre de pouls Nonin | Toutes les 15 sec | <92% | <88% |
| **Température Centrale** | Pilule thermomètre ingérable | Toutes les 5 min | >38.5°C | >39.5°C |
| **Température Cutanée** | Capteurs iButton (4 emplacements) | Toutes les 1 min | >37°C ou <32°C | >38°C ou <30°C |
| **Tension Batterie** | Télémétrie fauteuil | Toutes les 30 sec | <20% capacité | <10% capacité |
| **Température Moteur Fauteuil** | Capteurs thermiques | Toutes les 1 min | >65°C | >75°C |

### Surveillance Environnementale

| Paramètre | Capteur | Seuil d'Alerte | Réponse |
|-----------|---------|----------------|---------|
| **Détection Foudre** | Capteur Franklin AS3935 | Impact dans un rayon de 15 km | Protocole d'abri immédiat |
| **Température Ambiante** | Capteur DHT22 | >33°C avec humidité >80% | Pause refroidissement requise |
| **Vitesse du Vent** | Anémomètre | >40 km/h soutenu | Réévaluation d'itinéraire |
| **Indice UV** | Capteur VEML6075 | >8 (Très Élevé) | Réapplication SPF + ombre |

## Système d'Alerte Multi-Couches

### Niveau 1 : Conseil (Jaune)
**Déclencheur :** Un paramètre hors norme pendant >5 minutes

**Exemples :**
- Fréquence cardiaque 155-160 bpm soutenue
- SpO₂ 90-92%
- Batterie 20-25%

**Réponse :**
- Alerte sonore au leader d'expédition
- Rédacteur notifié via smartwatch
- Augmentation fréquence surveillance à toutes les 30 secondes
- Journalisation événement dans carnet de terrain

### Niveau 2 : Avertissement (Orange)
**Déclencheur :** Deux paramètres anormaux OU un paramètre en zone critique

**Exemples :**
- Fréquence cardiaque >160 bpm + température centrale >38.5°C
- Foudre détectée dans un rayon de 15 km
- Batterie <15%

**Réponse :**
- Arrêt immédiat requis
- Conducteur active protocole d'extraction
- Conseiller médical contacté via messager satellite
- Signes vitaux transmis toutes les 10 secondes
- Abri/hôpital le plus proche identifié sur carte

### Niveau 3 : Urgence (Rouge)
**Déclencheur :** Paramètre mettant la vie en danger OU perte de communication

**Exemples :**
- Fréquence cardiaque >180 bpm ou <35 bpm
- SpO₂ <88% pendant >2 minutes
- Température centrale >39.5°C
- Aucun signal télémétrie pendant >3 minutes

**Réponse :**
- Coordonnées GPS automatiques envoyées au conseiller médical
- Conducteur initie extraction d'urgence vers hôpital pré-cartographié
- SOS satellite activé si aucune réponse dans 5 minutes
- Contacts d'urgence notifiés automatiquement

## Points d'Extraction Pré-Cartographiés

### Côte Est (Segment Autoroute Su-Hua)

| Marqueur KM | Emplacement | Hôpital le Plus Proche | Distance | ETA par Van |
|-------------|-------------|----------------------|----------|-------------|
| **KM 112** | Aire de Repos Chongde | Hôpital Tzu Chi Hualien | 28 km | 35 min |
| **KM 145** | Canton de Xincheng | Hôpital Général Hualien | 15 km | 22 min |
| **KM 178** | Village de Nan'ao | Clinique de Nan'ao (stabilisation uniquement) | 2 km | 5 min |
| | → Transfert vers | Hôpital des Anciens Combattants Su-Ao | 18 km | 25 min |
| **KM 201** | Gare de Dong'ao | Hôpital des Anciens Combattants Su-Ao | 12 km | 18 min |
| **KM 234** | Zone Industrielle Heping | Hôpital Tzu Chi Hualien | 45 km | 55 min |

### Côte Ouest (Segment Urbain)

| Marqueur KM | Emplacement | Hôpital le Plus Proche | Distance | ETA par Van |
|-------------|-------------|----------------------|----------|-------------|
| **KM 45** | Centre-ville Kaohsiung | Hôpital Université Médicale Kaohsiung | 3 km | 8 min |
| **KM 89** | Ville de Tainan | Hôpital Université Nationale Cheng Kung | 5 km | 12 min |
| **KM 134** | Ville de Chiayi | Hôpital Mémorial Chang Gung | 8 km | 15 min |
| **KM 178** | Canton de Yunlin | Hôpital Chrétien Changhua | 22 km | 28 min |

## Structure de Supervision Médicale

### Conseiller Médical de Garde
- **Rôle :** Surveillance à distance et support décisionnel
- **Disponibilité :** 06h00-22h00 quotidien (heure Taïwan)
- **Communication :** Messager satellite + WhatsApp + téléphone
- **Qualifications :** Spécialiste médecine d'urgence avec expérience expédition

### Contacts d'Urgence Locaux
- **119 :** Services d'urgence Taïwan (ambulance/pompiers)
- **112 :** Numéro d'urgence universel (fonctionne sans SIM)
- **Lignes directes hôpitaux :** Préprogrammées pour chaque zone d'extraction

### Inventaire d'Équipement

| Article | Quantité | Emplacement |
|---------|----------|-------------|
| Défibrillateur Automatisé Externe (DAE) | 1 | Van d'assistance |
| Trousse médicaments d'urgence | 1 | Fauteuil + van |
| Concentrateur d'oxygène portable | 1 | Fauteuil |
| Packs batterie de secours (12V) | 4 | Van (2) + Fauteuil (2) |
| Messager satellite (Garmin inReach) | 2 | Leader + Conducteur |
| Trousse premiers secours (niveau sauvage) | 2 | Van + Fauteuil |

## Collecte de Données et Confidentialité

### Ce Que Nous Collectons
- Signes vitaux continus (FC, SpO₂, température)
- Position GPS et vitesse
- Conditions environnementales (météo, qualité de l'air)
- Métriques de performance équipement
- Scores bien-être subjectifs (auto-déclarés toutes les 4 heures)

### Comment Nous les Utilisons
- **Temps réel :** Surveillance sécurité et déclenchement alertes
- **Post-expédition :** Publication recherche médicale (anonymisée)
- **Open-source :** Données agrégées accessibilité et sécurité publiées sous Creative Commons

### Protection Confidentialité
- Toutes données santé personnelles chiffrées au repos et en transit
- Jeux de données publics anonymisés (aucun identifiant individuel)
- Conseiller médical lié par accord de confidentialité
- Conservation données : 5 ans post-expédition, puis suppression sécurisée

## Résultats Tests Terrain (Phase Pilote)

### Test : Taipei à Yilan (Mars 2026)
- **Distance :** 95 km
- **Durée :** 11 heures
- **Alertes déclenchées :** 3 (toutes Niveau 1 - conseil)
  - Pic fréquence cardiaque à 158 bpm (segment montée)
  - Alerte batterie à 22% (résolu avec charge solaire)
  - Alerte foudre à 18 km distance (protocole abri activé)

**Résultat :** Tous systèmes fonctionnels. Temps de réponse dans paramètres acceptables. Raffinements protocoles implémentés.

### Test : Kaohsiung à Tainan (Avril 2026)
- **Distance :** 48 km
- **Durée :** 5.5 heures
- **Conditions environnementales :** 34°C ambiant, 85% humidité
- **Alertes déclenchées :** 2 (Niveau 2 - avertissement)
  - Température centrale atteinte 38.7°C (pause refroidissement initiée)
  - SpO₂ descendu à 91% pendant 3 minutes (repos + oxygène)

**Résultat :** Protocole stress thermique validé. Mesures refroidissement supplémentaires ajoutées à équipement standard.

---

*Ce protocole est un document vivant. Les mises à jour sont publiées lorsque les tests terrain révèlent des opportunités d'optimisation. Dernière mise à jour : Juin 2026.*

*Questions sur les partenariats médicaux ou l'architecture de sécurité ? 
*Contact: [RollFree](mailto:rollfree142@gmail.com)*