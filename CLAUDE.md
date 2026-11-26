<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
-->

# CLAUDE.md — namfoop-hat

Carte d'extension Raspberry Pi 5 pour namfoop (basse, temps réel). **La fiabilité en live et la
latence priment sur tout**, comme dans namfoop. Doc utilisateur : `README.md`.

## Ce dépôt et namfoop

- namfoop voit la carte comme une carte ALSA plus un profil : ce dépôt ne modifie pas namfoop et
  n'y ouvre ni issue ni PR. Un profil de carte ou un pilote à ajouter côté namfoop se demande à
  l'utilisateur.
- Ce que namfoop sait déjà (profils de carte, latence), on le lit dans son guide au lieu de le
  redécrire.

## Carte

```
hardware/   KiCad, Gerber, BOM                   CERN-OHL-S-2.0
firmware/   overlay device tree, EEPROM HAT+     GPL-3.0-or-later
scripts/    un script par geste                  GPL-3.0-or-later
docs/       cahier des charges, décisions,      CC-BY-SA-4.0
            style des issues, montage, mesures
docs/identite/  copies des images de namfoop   tous droits réservés
```

## Licences (non négociables)

- Chaque fichier a sa licence SPDX : en-tête, ou `REUSE.toml` pour ce qui n'en accepte pas.
  `reuse lint` doit passer (la CI le vérifie).
- Le nom et l'identité visuelle namfoop sont tous droits réservés (`LicenseRef-TousDroitsReserves`,
  `TRADEMARKS.md`) : `docs/identite/` en est une copie conforme du dépôt namfoop, qui fait
  référence ; ne jamais les redessiner ici. Le logo de sérigraphie reste une empreinte séparée.
- Chaque fichier écrit porte `SPDX-FileCopyrightText: © <année> les auteurs de namfoop-hat
  (AUTHORS.md)` ; un contributeur s'ajoute à `AUTHORS.md`.
- La sérigraphie porte la Source Location, la licence et la révision (`NOTICE`).
- Reprendre un fichier d'ailleurs : licence compatible avec le dossier, en-tête d'origine gardé,
  texte ajouté dans `LICENSES/`.
- Rien ne versionne un son, un modèle, une IR, une police ni une fiche technique.
- Cédric Boufflers est le titulaire du nom et de l'identité, et le mainteneur du CLA (personne
  physique). La marque n'est pas enregistrée : jamais de ®.

## Cycle

issue → branche (`feat|fix|docs/<n°>-…`) → PR « Closes #n » → CI verte → squash merge. Jamais de
commit direct sur `main`. Un agent n'a ni carte ni banc : il vérifie ERC/DRC et `--dry-run`, et
demande l'essai matériel à l'utilisateur (étiquette `essai-materiel`).

**Les issues s'écrivent pour le bassiste** : [`docs/style-issues.md`](docs/style-issues.md), skill
`ecrire-issue`. Types : `epic`, `etude`, `story`, `chore`, `bug`, plus un domaine (`audio`, `midi`,
`alimentation`, `mecanique`, `commandes`, `logiciel`). Pas de référence de composant ni de nom de
signal dans le corps : le technique va dans un commentaire `## Cadrage technique`, à lire avant de
travailler.

**On décide avant de dessiner.** Une `etude` se cadre avec l'utilisateur (une proposition par
question, jamais seul) et se ferme par une décision dans `docs/decisions/` et le
[cahier des charges](docs/cahier-des-charges.md) mis à jour. Une décision ne se rouvre que sur une
mesure ou un fait nouveau.

## Conventions

- Tout en **français** ; identifiants en anglais.
- Un fait mesuré donne la révision de la carte, le banc et la date, et **remplace** le précédent.
