<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
-->

# Contribuer à namfoop-hat

Merci de vouloir améliorer la carte. Tout se passe en français : issues, commits, documentation,
commentaires ; les identifiants (noms de signaux, de fichiers, de variables) en anglais.

## L'accord de contributeur, d'abord

Avant qu'une première contribution soit fusionnée, il faut accepter
l'[accord de contributeur](CLA.md) (CLA). Il vous laisse auteur de votre travail et garantit qu'il
restera disponible sous licence libre ; il permet au mainteneur de proposer aussi la carte sous une
autre licence (double licence). On l'accepte une fois, en cochant la case de la description de PR.

## Le cycle

**issue → branche → PR → CI verte → squash merge.** Jamais de commit direct sur `main`.

- Une **issue** dit ce que le bassiste veut pouvoir faire, ou ce qui ne va pas, et finit par une
  rubrique « Terminé quand » qui s'observe sur la carte ou au banc. Étiquettes : `epic`, `story`,
  `etude` (à trancher avant de dessiner ou de coder), `chore`, `bug`.
- Une **branche** par issue : `feat|fix|docs/<n°>-…`.
- La **PR** dit « Closes #n » et coche l'accord de contributeur.

## Les licences, par dossier

Un fichier versé dans un dossier prend la licence de ce dossier (voir la section Licence du
[README](README.md)) :

| Dossier | Licence | En-tête |
| :--- | :--- | :--- |
| `hardware/` | CERN-OHL-S-2.0 | dans le cartouche KiCad (voir `hardware/README.md`), sinon `REUSE.toml` |
| `firmware/`, `scripts/` | GPL-3.0-or-later | en tête de chaque fichier source |
| `docs/` et les `.md` | CC-BY-SA-4.0 | commentaire HTML en tête du fichier |
| images de `docs/identite/`, logo de sérigraphie | tous droits réservés | `REUSE.toml` ; on ne les modifie pas ici |

L'en-tête d'un fichier qu'on écrit :

<!-- REUSE-IgnoreStart -->
```sh
# SPDX-License-Identifier: GPL-3.0-or-later
# SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
```
<!-- REUSE-IgnoreEnd -->

`reuse lint` (<https://reuse.software>) vérifie que chaque fichier a sa licence ; la CI le lance.

**Reprendre un fichier d'un autre projet** (empreinte, symbole, modèle 3D, overlay, script) :
seulement si sa licence est compatible avec celle du dossier qui le reçoit, en gardant son en-tête
et son auteur, et en ajoutant son texte de licence dans `LICENSES/`. Une empreinte ou un symbole
des bibliothèques officielles de KiCad peut s'utiliser dans la carte (exception de leur licence
CC-BY-SA-4.0) ; les copier dans `hardware/` en tant que bibliothèque garde leur licence.

## Ce qu'on ne versionne pas

- Aucun son, modèle NAM, IR, ni police : leurs droits appartiennent à leurs auteurs.
- Aucune fiche technique de fabricant (PDF) : on donne le lien.
- Les sorties de fabrication seulement pour une révision publiée, dans
  `hardware/fabrication/<révision>/`.

## Une carte qu'on modifie

Une révision qui change le circuit met à jour la révision de la sérigraphie et garde la Source
Location (voir [`NOTICE`](NOTICE)). Une carte dérivée publiée ailleurs y met l'adresse de sa propre
source et retire le nom et le logo namfoop ([`TRADEMARKS.md`](TRADEMARKS.md)).
