<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
-->

# Style des issues

La backlog se lit **sans ouvrir le schéma**. Une issue dit ce que le bassiste pourra faire, ou ce
qu'il faut décider, et à quoi on verra que c'est fait ; le détail technique vit à côté, dans un
commentaire. Adapté du style de namfoop (`docs/style-issues.md` de namfoop) : même esprit, plus le
type `etude`, parce qu'une carte se décide avant de se dessiner.

## Cinq types, une étiquette chacun

| Étiquette | Ce que c'est | Se termine par |
|---|---|---|
| `epic` | un grand résultat : il regroupe des études ou des stories et dit où on en est | ses cases cochées |
| `etude` | une question à trancher avant de dessiner ou de coder | une décision écrite dans [`decisions/`](decisions/) |
| `story` | ce que le bassiste veut pouvoir faire avec la carte | une PR : schéma, circuit, overlay, script |
| `chore` | atelier : outillage, CI, documentation, sans effet sur la carte | une PR |
| `bug` | un comportement incorrect de la carte ou de ses outils | une PR, ou une révision |

Une issue porte **exactement une** de ces étiquettes. S'y ajoutent au besoin :

- **un domaine**, au plus deux : `audio`, `midi`, `alimentation`, `mecanique`, `commandes`,
  `logiciel` (reconnaissance par le Pi, overlay, EEPROM, profil namfoop) ;
- `needs-refinement` : une story ou une épique encore trop floue pour s'y lancer ;
- `essai-materiel` : un essai sur la carte ou au banc reste à faire par l'utilisateur (un agent n'a
  ni carte ni banc).

## Le titre

Ce que je peux faire, ou ce qu'il faut choisir, **dans les mots de celui qui joue** : « Brancher mon
pédalier MIDI sur la carte », pas « UART RP1 à 31 250 bauds vers snd-serial ». Ni référence de
composant, ni nom de signal ou de broche, ni chemin de fichier. Les mots du musicien sont permis :
XLR, jack, DIN, haute impédance, dBu, latence en ms.

## Le corps

**Étude**

```markdown
**Question.** Une phrase : ce qu'on doit décider.

## Pourquoi ça compte
2 à 4 phrases : ce que je branche, entends ou transporte, ce qui peut rater sur scène.

## Ce qu'on sait déjà
Les faits établis : décisions prises, ce que namfoop fait déjà.

## À trancher
- [ ] une question courte par case, avec la proposition par défaut si on en a une

## Terminé quand
- [ ] chaque point de « À trancher » a sa réponse, écrite dans une décision du dépôt
- [ ] le cahier des charges porte les chiffres retenus

## Liens
Épique, dépend de, pèse sur.
```

**Story**

```markdown
**En tant que** bassiste <situation>, **je veux** <ce que je fais>, **afin de** <le bénéfice>.

## Aujourd'hui
## Terminé quand        (3 à 6 critères observables, sur la carte ou au banc)
## Hors périmètre
## À trancher           (seulement s'il reste une vraie décision)
## Liens
```

**Épique** : deux ou trois phrases sur ce que le résultat change, puis `## Où on en est`,
`## Études` ou `## Stories` (une case par issue, cochée quand elle est fermée),
`## Décisions déjà prises` (en mots simples, avec le lien vers la décision), `## Ensuite`,
`## Plus tard, peut-être`.

**Chore** : `## Pourquoi`, `## Terminé quand`, `## Liens`.

**Bug** : `## Ce qui se passe`, `## Ce qui devrait se passer`, `## Contexte` (révision de la carte,
Pi, noyau, version de namfoop).

Les modèles de [`.github/ISSUE_TEMPLATE/`](../.github/ISSUE_TEMPLATE/) portent ces rubriques.

## Ce qui n'entre pas dans le corps

- une référence de composant, un nom de signal, de broche ou de GPIO, un chemin de fichier ;
- les pistes techniques, les calculs, les mesures de banc ;
- des consignes à l'agent qui réalise.

Tout cela va dans le **cadrage technique** : un commentaire de l'issue qui commence par
`## Cadrage technique`. C'est lui que lit l'agent avant de chercher ou de dessiner. Une précision
qui arrive en cours de route s'ajoute en commentaire, pas dans le corps.

## Cadrer une étude

1. Lire le corps, le cadrage technique et les commentaires.
2. Chercher : fiches techniques (on donne le lien, on ne les versionne pas), pilotes Linux, cartes
   du commerce qui ont déjà résolu la question. Ce qu'on trouve s'ajoute en commentaire.
3. Poser à l'utilisateur les questions de « À trancher », peu à la fois, chacune avec une réponse
   proposée et ce qu'elle implique. **L'agent ne tranche pas seul.**
4. Chaque réponse coche sa case, et rejoint une décision de [`decisions/`](decisions/) et le
   [cahier des charges](cahier-des-charges.md).
5. Une PR « Closes #n » livre la décision et le cahier des charges mis à jour. Une question qui
   naît en chemin devient une nouvelle étude, rattachée à l'épique, qui gagne une case.

## Écrire

- Première personne (« je »), phrases simples, vocabulaire du musicien.
- Les faits et chiffres parlants se gardent : « environ 5 ms aller-retour avec la carte USB ».
- Un critère de « Terminé quand » s'observe sans ouvrir le schéma : sur la carte, au banc, dans le
  dépôt.
- Court : une issue tient en 15 à 30 lignes.

## Créer une issue

Écrire le corps et le cadrage dans deux fichiers, puis :

```sh
gh issue create --label etude --label audio --title "Titre" --body-file corps.md
gh issue comment <n°> --body-file cadrage.md
```

puis ajouter la case dans l'épique.
