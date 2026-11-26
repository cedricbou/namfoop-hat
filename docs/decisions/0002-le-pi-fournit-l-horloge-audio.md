<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
-->

# 0002 · Horloge audio : le Pi la fournit, à 48 kHz seulement

**Statut : adoptée, à confirmer par la mesure du prototype.**
**Étude :** #5

**Contexte.** Tous les convertisseurs doivent suivre une seule horloge, et sa qualité s'entend.
La [décision 0001](0001-deux-codecs-stereo-regles-par-broches.md) retient deux TAC5242, qui
savent recevoir l'horloge sans MCLK. Le Pi 5 fabrique BCLK à partir de son quartz de 50 MHz, par
une boucle à verrouillage de phase réservée à l'audio, en mode fractionnaire à 48 kHz
(`drivers/clk/clk-rp1.c` du noyau du Pi). Aucune mesure publiée de sa gigue n'a été trouvée.

**Options étudiées.**
- Le Pi fournit BCLK et LRCLK : aucun composant en plus, montage des cartes 8 canaux déjà prises
  en charge par le noyau, filtre faible latence du TAC5242 disponible. Qualité : celle de la
  boucle du Pi, repassée par celle de chaque puce.
- Un TAC5242 fournit l'horloge à partir d'un oscillateur de 36,864 MHz : horloge propre, mais ce
  mode impose le filtre à phase linéaire, donc plus de retard
  ([fiche](https://www.ti.com/lit/pdf/SLASF27), section 7.3.1).
- Un oscillateur et une puce d'horloge cadencent les deux TAC5242 et le Pi : horloge propre et
  filtre faible latence, au prix de composants en plus et d'un overlay où le Pi reçoit l'horloge.

**Décision.**
- Le Pi fournit BCLK (3,072 MHz) et LRCLK (48 kHz) aux deux puces. Pas d'oscillateur sur la carte.
- 48 kHz seulement : c'est la fréquence de namfoop, et les puces sont réglées par broches pour
  elle.

**Conséquences.**
- Coût : aucun composant, aucune place, aucun overlay particulier.
- L'horloge ne tourne que lorsqu'un programme tient la carte ouverte ; les puces s'éteignent et se
  rallument avec elle. Le bruit de commutation en sortie se traite avec les sorties (#7).
- Le prototype (#15) mesure le plancher de bruit sous une sinusoïde à pleine échelle, à 1 kHz et à
  10 kHz, sortie rebouclée sur entrée.

**Estimation, en attendant la mesure.** Tenir 105 dB sous un signal à pleine échelle demande moins
de 900 ps de gigue efficace à 1 kHz et moins de 180 ps à 5 kHz. Une boucle de ce genre en donne
d'ordinaire quelques dizaines : la marge est large pour une basse.

**Ce qui la rouvrirait.** Sur le prototype, un plancher de bruit sous signal qui passe sous
l'objectif de 105 dB alors qu'il est tenu au repos. Le montage avec oscillateur utilise les mêmes
broches du Pi : y passer demande une révision de la carte, pas une refonte.
