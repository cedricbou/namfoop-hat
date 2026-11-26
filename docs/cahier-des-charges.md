<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
-->

# Cahier des charges

**Brouillon.** Ce que la carte doit faire, en chiffres, au fur et à mesure que les études tranchent.
Chaque ligne « à trancher » renvoie à son étude ; une fois décidée, elle prend sa valeur et le lien
vers la [décision](decisions/). Le pourquoi est dans la décision, pas ici.

## Ce que c'est

Une carte d'extension pour Raspberry Pi 5 qui remplace la carte son USB sur scène : la basse et
d'autres sources entrent, namfoop les traite, le son part au sondier et dans les in-ears, et le
pédalier MIDI pilote le tout.

## Déjà décidé

| | Valeur | Pourquoi |
|---|---|---|
| Machine | Raspberry Pi 5, connecteur 40 broches | la machine de scène de namfoop |
| Vue par namfoop | une carte son Linux (ALSA) plus un profil, sans code dans namfoop | décision 0003 de namfoop |
| Fréquence | 48 kHz | les modèles de namfoop sont entraînés à 48 kHz |
| Latence aller-retour | pas pire qu'avec la carte USB : environ 5 ms, mesurée par `namfoop latency` | la latence prime |
| Liaison audio | I2S du connecteur 40 broches | le chemin le plus court vers le processeur |
| Convertisseurs | deux codecs stéréo TAC5242 réglés par broches, sans pilote | [décision 0001](decisions/0001-deux-codecs-stereo-regles-par-broches.md) |
| Chemin vers le Pi | deux lignes I2S d'entrée et deux de sortie, horloge fournie par le Pi | [décision 0001](decisions/0001-deux-codecs-stereo-regles-par-broches.md) |
| Carte son | une seule, 4 entrées et 4 sorties, 48 kHz, mots de 32 bits | [décision 0001](decisions/0001-deux-codecs-stereo-regles-par-broches.md) |
| Retard des convertisseurs | filtre faible latence : environ 0,3 ms aller-retour, à mesurer sur le prototype | [décision 0001](decisions/0001-deux-codecs-stereo-regles-par-broches.md) |
| Bruit de fond | 105 dB de dynamique (pondération A), sortie rebouclée sur entrée | [décision 0001](decisions/0001-deux-codecs-stereo-regles-par-broches.md) |
| Niveau à la puce | 2 Vrms en symétrique, environ +8 dBu, en entrée comme en sortie | [décision 0001](decisions/0001-deux-codecs-stereo-regles-par-broches.md) |
| Montage et achat | pochoir et air chaud, pas de BGA ; composants en stock chez Mouser | `CLAUDE.md` |

## À trancher

| Sujet | Demande de départ | Étude |
|---|---|---|
| Horloge audio | — | #5 |
| Entrées | 4 entrées symétriques ; la basse demande une haute impédance | #6 |
| Sorties | 4 sorties symétriques : sondier, in-ears | #7 |
| Format, prises, boîtier | — | #8 |
| MIDI | entrée, sortie, thru | #9 |
| Alimentation | une seule prise sur scène | #10 |
| Reconnaissance par le Pi et namfoop | — | #11 |
| Boutons et voyants | en bonus | #12 |

L'épique de cadrage (#3) suit l'ensemble.
