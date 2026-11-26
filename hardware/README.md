<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: 2026 les contributeurs de namfoop-hat
-->

# hardware/ — la carte

Sous **CERN-OHL-S-2.0** ([`LICENSE`](../LICENSE)). Conçue avec **KiCad**.

```
hardware/
  namfoop-hat.kicad_pro    le projet KiCad (schéma .kicad_sch, circuit .kicad_pcb)
  bibliotheque/            symboles, empreintes, modèles 3D propres à la carte
  fabrication/<révision>/  Gerber, perçages, BOM, placement : seulement pour une révision publiée
```

## Les Notices dans le dessin

Chaque feuille du schéma et le circuit portent, dans leur cartouche (champs « Commentaire ») :

<!-- REUSE-IgnoreStart -->
```
SPDX-License-Identifier: CERN-OHL-S-2.0
SPDX-FileCopyrightText: 2026 les contributeurs de namfoop-hat
Source: github.com/cedricbou/namfoop-hat
```
<!-- REUSE-IgnoreEnd -->

La **sérigraphie** porte, lisiblement et sur une face visible une fois la carte montée :

```
Source: github.com/cedricbou/namfoop-hat
CERN-OHL-S-2.0  rev X.Y
```

C'est une exigence de la licence pour toute carte fabriquée (voir [`NOTICE`](../NOTICE)) ; la
révision change à chaque modification du circuit.

Le **logo namfoop** est une empreinte à part (`bibliotheque/`, sans connexion électrique), pour
qu'une carte dérivée le retire sans toucher au reste ([`TRADEMARKS.md`](../TRADEMARKS.md)).

## Composants

La BOM donne pour chaque composant une référence de fabricant et au moins une source. Les
composants du commerce sont des « Available Components » au sens de la licence : on publie leur
référence, pas leur conception. Les fiches techniques ne sont pas versionnées : on donne leur lien.

## Une révision publiée

1. ERC et DRC KiCad sans erreur.
2. Révision mise à jour dans le cartouche et sur la sérigraphie.
3. Sorties générées dans `fabrication/<révision>/` (Gerber, perçages, BOM, placement).
4. Tag `hw-vX.Y` sur le commit.
