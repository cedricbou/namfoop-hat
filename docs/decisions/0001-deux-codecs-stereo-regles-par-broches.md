<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
-->

# 0001 · Chemin audio : deux codecs stéréo réglés par broches, sur deux lignes I2S du Pi

**Statut : adoptée.**
**Étude :** #4

**Contexte.** Il faut 4 entrées et 4 sorties à 48 kHz, vues par namfoop comme une seule carte son,
sans latence ajoutée et sans rien à maintenir côté Linux. Le Pi 5 offre l'I2S sur quatre lignes
stéréo d'entrée et quatre de sortie qui partagent BCLK et LRCLK ; il n'a ni TDM ni MCLK
([livre blanc I2S de Raspberry Pi](https://pip-assets.raspberrypi.com/categories/1259-audio-camera-and-display/documents/RP-009699-WP-1-Using%20the%20I2S%20peripherals%20on%20Raspberry%20Pi%20SBCs.pdf),
février 2026). La révision 1 se soude au pochoir et à l'air chaud, et tout s'achète chez Mouser.

**Options étudiées.**
- Un codec 4 / 4 sur une seule ligne (AK4619) : écarté, il lui faut le TDM, et son pilote n'est pas
  compilé dans le noyau du Pi.
- Une puce pilotée par Linux (PCM3168A) : pilote présent dans le noyau du Pi, mais 64 broches, un
  oscillateur sur la carte et un réglage par I2C à faire vivre.
- Deux codecs stéréo pilotés par Linux (PCM3060, CS4272) : pilotes absents du noyau du Pi, donc un
  module à recompiler à chaque mise à jour.
- Convertisseurs séparés réglés par broches ([PCM1861](https://www.ti.com/product/PCM1861) et
  [PCM5102A](https://www.ti.com/product/PCM5102A)) : tout à pattes, 110 et 112 dB, mais quatre
  puces, des sorties à symétriser, et le PCM1861 exige un MCLK, donc un oscillateur sur la carte
  qui donne l'horloge au Pi. Stock du PCM1861 faible.
- Deux codecs stéréo réglés par broches ([TAC5242](https://www.ti.com/product/TAC5242)) : 119 dB
  en entrée et 120 dB en sortie, symétrique natif, pas de MCLK, filtre faible latence, mais un
  boîtier sans pattes (VQFN 24, pas de 0,5 mm).

**Décision.**
- Deux TAC5242, réglés par leurs broches : receveurs d'horloge en I2S, 3,3 V, mots de 32 bits,
  filtre faible latence, entrées et sorties différentielles.
- Le Pi fournit BCLK (GPIO18) et LRCLK (GPIO19) aux deux puces ; la première occupe les lignes de
  données GPIO20 et GPIO21, la seconde GPIO22 et GPIO23. Une seule carte son de 4 entrées et
  4 sorties, sur une seule horloge.
- Aucun pilote de convertisseur : la carte se déclare avec un codec factice, comme les cartes
  8 canaux déjà prises en charge par le noyau du Pi.
- Bruit de fond visé pour la carte finie : 105 dB de dynamique (pondération A), mesurés sortie
  rebouclée sur entrée.

**Conséquences.**
- Horloge (#5) : le Pi est la source ; l'étude porte sur la qualité de cette horloge, plus sur un
  oscillateur.
- Entrées (#6) et sorties (#7) : la puce accepte et délivre 2 Vrms en différentiel (environ
  +8 dBu) et présente 5 kΩ par broche ; l'adaptation de niveau et la haute impédance pour la basse
  se font devant elle.
- Reconnaissance (#11) : un overlay à nous, sur le modèle de celui des cartes 8 canaux ; GPIO24 à
  GPIO27 restent libres.
- Montage : un boîtier sans pattes, permis par la règle « Composants » du `CLAUDE.md`.
- namfoop : un profil de carte, rien d'autre.

**Relevé Mouser** (26/11/2026, mouser.com) : TAC5242IRGER, 1 713 en stock, 7,83 $ à l'unité,
6,04 $ par 10.

**Ce qui la rouvrirait.** Sur le prototype, une latence aller-retour mesurée par
`namfoop --backend alsa latency` pire que les 5 ms de la carte USB ; une horloge du Pi qui dégrade
le bruit sous l'objectif ; le TAC5242 introuvable chez Mouser.
