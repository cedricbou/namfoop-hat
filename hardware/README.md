<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
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
SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
Source: github.com/cedricbou/namfoop-hat
```
<!-- REUSE-IgnoreEnd -->

La **sérigraphie** porte, lisiblement et sur une face visible une fois la carte montée :

```
namfoop-hat rev X.Y  © 2026 [NOM DU TITULAIRE]
Source: github.com/cedricbou/namfoop-hat
CERN-OHL-S-2.0
```

C'est une exigence de la licence pour toute carte fabriquée (voir [`NOTICE`](../NOTICE)) ; la
révision change à chaque modification du circuit.

Le **logo namfoop** est une empreinte à part, sans connexion électrique :
`bibliotheque/namfoop-hat.pretty/Logo_namfoop_30mm.kicad_mod` (30 × 5,1 mm, sérigraphie du
dessus, tracé depuis `docs/identite/logo-sombre.svg`). À cette taille, la barre la plus fine
fait 0,42 mm et le vide entre deux barres 0,32 mm : avant de le réduire, vérifier le minimum de
sérigraphie du fabricant. L'empreinte est **tous droits réservés**,
pas sous CERN-OHL-S : une carte dérivée la supprime sans toucher au reste
([`TRADEMARKS.md`](../TRADEMARKS.md)).

## Composants

La BOM donne pour chaque composant une référence de fabricant et au moins une source. Les
composants du commerce sont des « Available Components » au sens de la licence : on publie leur
référence, pas leur conception. Les fiches techniques ne sont pas versionnées : on donne leur lien.

## Une révision publiée

1. ERC et DRC KiCad sans erreur.
2. Révision mise à jour dans le cartouche et sur la sérigraphie.
3. Sorties générées dans `fabrication/<révision>/` (Gerber, perçages, BOM, placement).
4. Tag `hw-vX.Y` sur le commit.
