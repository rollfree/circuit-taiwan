---
title: "Sécurité : Fauteuil Roulant et détection de foudre sur la côte taïwanaise"
description: "Comment le système de sécurité intégré et hors ligne de Circuit Taiwan utilise la détection de foudre et la télémétrie biométrique pour protéger un usager vulnérable de la route sur l'autoroute Su-Hua."
summary: "Lorsque le service cellulaire disparaît dans un tunnel et qu'une tempête subtropicale arrive, une application météo sur smartphone est inutile. Voici comment nous construisons un système d'alerte précoce hors ligne et multicouche pour garder l'expédition en sécurité."
date: 2026-06-19
draft: false
tags: ["sécurité", "ingénierie", "détection-de-foudre", "autoroute-su-hua", "technologie"]
toc: true
---

Il y a vingt-cinq ans, j'ai parcouru l'autoroute Su-Hua en voiture. Quand une tempête approchait, j'allumais les essuie-glaces, je ralentissais peut-être un peu, et je continuais à rouler. J'avais un toit en métal, la climatisation, et la capacité d'accélérer pour sortir d'une situation difficile.

En septembre 2027, je tenterai le même parcours en fauteuil roulant électrique.

La différence de vulnérabilité est massive. Un utilisateur de fauteuil roulant est près du sol, physiquement exposé aux éléments, et se déplace à une fraction de la vitesse du trafic motorisé. Quand un orage subtropical arrive sur le Pacifique, « trouver un abri » n'est pas une question d'accélération. C'est une question de savoir que la tempête arrive bien avant que la première goutte de pluie ne tombe.

C'est pourquoi Circuit Taiwan construit un système de sécurité et d'alerte précoce personnalisé, capable de fonctionner hors ligne.

### Le problème : Zones mortes sur le Su-Hua

Le projet d'amélioration de l'autoroute Su-Hua (蘇花改), achevé en 2021, a rendu le parcours viable pour les voyages lents non motorisés. Mais il a aussi créé de longues sections de tunnels où le service cellulaire disparaît.

La plupart des gens comptent sur les applications météo de leur smartphone. Mais quand le signal LTE disparaît dans un tunnel, votre radar météo devient vierge. Au moment où vous pouvez physiquement voir la tempête, vous êtes déjà dedans. Nous ne pouvons pas compter sur le cloud. Nous avons besoin de vérités terrain.

### La solution : Sécurité multicouche et hors ligne

Notre système de sécurité intégré fonctionne entièrement indépendamment d'Internet ou des réseaux mobiles. Il s'appuie sur trois couches de données locales :

**1. Vérités terrain locales (Le Matériel)**
Nous intégrons une **unité de détection de foudre** dédiée capable de détecter les frappes jusqu'à 40 km, couplée à une **station météo compacte** mesurant la pression atmosphérique, la température et l'humidité.
*   *La logique :* Une chute rapide de la pression barométrique est l'indicateur physique le plus fiable d'une cellule orageuse approchante. Si la pression chute et que le détecteur de foudre émet un signal, nous avons la preuve physique du danger, quel que soit le réseau cellulaire.

**2. Retour biométrique (Le Corps)**
Une smartwatch de qualité médicale surveillera en continu la fréquence cardiaque, la variabilité de la fréquence cardiaque (VFC), la saturation en oxygène du sang (SpO2) et la température cutanée.
*   *La logique :* Dans une chaleur de 35°C et 90% d'humidité, la fatigue physique et le stress thermique peuvent altérer la prise de décision avant que le cerveau ne l'enregistre consciemment. La montre agit comme un système d'alerte précoce pour les limites physiques du conducteur.

**3. Le co-pilote IA (Le Cerveau)**
C'est là que le matériel rencontre l'intelligence. Toutes ces données sont alimentées dans un module d'IA en edge computing monté directement sur le fauteuil roulant.
*   *La logique :* L'IA calcule la probabilité d'intersection de la cellule orageuse par rapport à notre vitesse et notre cap actuels. Elle ne se contente pas de dire « tempête à proximité ». Elle calcule *quand* la tempête intersectera notre position exacte, donnant à l'équipe le temps précis pour exécuter une extraction.

### Le protocole d'alerte

Les données sont inutiles si elles n'atteignent pas l'humain. En roulant, le bruit du vent, l'écho des tunnels et la pluie sur le casque peuvent masquer les alarmes audio. Par conséquent, le système d'alerte est multisensoriel :

*   **CLAIR (CLEAR) :** Opération normale.
*   **VEILLE (WATCH) :** Vibration douce dans le coussin du siège et repère visuel sur la smartwatch. L'équipe commence à identifier l'abri le plus proche.
*   **ALERTE (WARNING) :** Vibration continue, alarme audio et invite vocale. Le véhicule d'assistance se met en position.
*   **DANGER :** Alarme maximale. CHERCHEZ UN ABRI MAINTENANT. Le véhicule ouvre ses portes immédiatement. Le conducteur est chargé dans la camionnette en quelques secondes.
*   **TYPHON :** Pause complète de l'expédition. Aucune reprise tant que l'Administration centrale de la météo (CWA) n'a pas donné le feu vert.

### Limites honnêtes

Nous testons des lunettes intelligentes avec un affichage tête haute pour les alertes visuelles. Cependant, sous le soleil direct et aveuglant de la côte taïwanaise, une superposition visuelle est incroyablement difficile à lire. La vibration physique dans le siège et la smartwatch au poignet restent nos mécanismes de sécurité les plus fiables. La technologie doit servir la réalité de l'environnement, et non l'inverse.

### L'objectif ultime : Sécurité open-source

Ce système est construit pour me garder en sécurité sur l'autoroute Su-Hua en 2027. Mais l'objectif ultime est beaucoup plus vaste.

À la fin de l'expédition, la conception technique, les journaux de fusion de capteurs, les benchmarks d'inférence hors ligne et les protocoles de sécurité seront publiés en tant que **cadre de sécurité open-source**.

Nous voulons prouver qu'avec l'edge computing moderne et des capteurs localisés, nous pouvons créer un filet de sécurité pour les usagers vulnérables de la route—qu'ils soient en fauteuil roulant, à vélo ou à pied—qui ne nécessite pas de signal cellulaire pour les garder en vie.

---

*Lisez cet article en [English](/en/posts/safety-lightning-detection/) ou en [繁體中文](/zh/posts/safety-lightning-detection/).*