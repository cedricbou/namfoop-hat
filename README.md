<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: 2026 les contributeurs de namfoop-hat
-->

# namfoop-hat

Une carte d'extension pour **Raspberry Pi 5** qui donne à [namfoop](https://github.com/cedricbou/namfoop)
ce qu'il faut pour jouer de la basse sur scène, sans carte son USB. Elle se branche sur le
connecteur 40 broches du Pi ; namfoop la voit comme une carte son ALSA munie de son profil.

**État : en conception.** Le cahier des charges (entrées, sorties, alimentation, commandes) s'écrit
dans [`docs/`](docs/) avant le premier schéma.

## Ce que contient le dépôt

```
hardware/      la carte : schéma et circuit KiCad, Gerber, nomenclature (BOM)   CERN-OHL-S-2.0
firmware/      ce qui tourne pour la carte : overlay device tree, EEPROM          GPL-3.0-or-later
scripts/       outils : fabrication, contrôle, flashage de l'EEPROM               GPL-3.0-or-later
docs/          cahier des charges, guide de montage, mesures                     CC-BY-SA-4.0
LICENSES/      le texte de chaque licence
```

Chaque dossier a son `README.md` : ce qu'on y range et comment.

## Licence

Ce dépôt réunit trois sortes d'œuvres, chacune sous une licence libre faite pour elle. Tout fichier
porte son identifiant SPDX, dans un en-tête ou, pour les fichiers qui n'en acceptent pas (KiCad,
Gerber, images), dans [`REUSE.toml`](REUSE.toml) ; `reuse lint` le vérifie à chaque PR.

| Dossier | Licence | Texte |
| :--- | :--- | :--- |
| `hardware/` | CERN Open Hardware Licence v2, Strongly Reciprocal (**CERN-OHL-S-2.0**) | [`LICENSE`](LICENSE), [`LICENSES/CERN-OHL-S-2.0.txt`](LICENSES/CERN-OHL-S-2.0.txt) |
| `firmware/`, `scripts/` | **GPL-3.0-or-later**, comme namfoop | [`LICENSES/GPL-3.0-or-later.txt`](LICENSES/GPL-3.0-or-later.txt) |
| `docs/` et les `.md` | Creative Commons Attribution-Partage dans les mêmes conditions 4.0 (**CC-BY-SA-4.0**) | [`LICENSES/CC-BY-SA-4.0.txt`](LICENSES/CC-BY-SA-4.0.txt) |

Le fichier `LICENSE` à la racine est celui de la carte, l'œuvre principale du dépôt.

**Ce que ça permet.** Tout le monde peut étudier la carte, la modifier, la faire fabriquer et la
vendre. En échange, qui distribue une carte, modifiée ou non, en donne la source complète sous la
même licence, ou indique où la trouver (CERN-OHL-S, section 4). Les composants du commerce (le Pi,
les circuits intégrés, les connecteurs) sont des « Available Components » : la licence ne demande
pas leur source.

**Source Location.** La source de la carte est publiée ici :

```
https://github.com/cedricbou/namfoop-hat
```

Au sens de la section 4 de la CERN-OHL-S, **toute carte fabriquée affiche sa Source Location sur
sa sérigraphie**, lisiblement, avec la licence et la révision. Le texte à tracer, à garder sur une
carte dérivée en y mettant l'adresse de sa propre source :

```
Source: github.com/cedricbou/namfoop-hat
CERN-OHL-S-2.0  rev X.Y
```

Ce rappel fait partie des Notices de la carte (voir [`NOTICE`](NOTICE)) : une version modifiée ne
le retire pas, elle le met à jour.

**Le nom et le logo n'en font pas partie.** « namfoop », son logo et son icône sont réservés et ne
sont couverts par aucune des trois licences : une carte dérivée vit sous son propre nom. Ce qui est
permis (dire « compatible namfoop », par exemple) est détaillé dans
[`TRADEMARKS.md`](TRADEMARKS.md).

**Vendre une carte avec namfoop installé.** Le Pi, sa carte SD et namfoop forment alors une
distribution de binaires GPL : joindre la licence de namfoop et un lien vers la source exacte du tag
installé, ainsi que la source de l'overlay et de l'EEPROM de `firmware/`.

**Contribuer.** Toute contribution passe par l'accord de contributeur décrit dans
[`CONTRIBUTING.md`](CONTRIBUTING.md) : il permet de proposer plus tard la carte sous une autre
licence en plus de celles-ci, sans retirer à personne ce que les licences libres accordent.

Raspberry Pi est une marque de Raspberry Pi Ltd. namfoop-hat n'est ni affilié à Raspberry Pi Ltd,
ni approuvé par elle.
