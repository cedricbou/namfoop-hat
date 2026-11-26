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

## À trancher

| Sujet | Demande de départ | Étude |
|---|---|---|
| Convertisseurs et chemin vers le Pi | 4 entrées, 4 sorties, une seule carte son | #4 |
| Horloge audio | — | #5 |
| Entrées | 4 entrées symétriques ; la basse demande une haute impédance | #6 |
| Sorties | 4 sorties symétriques : sondier, in-ears | #7 |
| Format, prises, boîtier | — | #8 |
| MIDI | entrée, sortie, thru | #9 |
| Alimentation | une seule prise sur scène | #10 |
| Reconnaissance par le Pi et namfoop | — | #11 |
| Boutons et voyants | en bonus | #12 |

L'épique de cadrage (#3) suit l'ensemble.
