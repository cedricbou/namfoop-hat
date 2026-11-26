<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
-->

# docs/decisions/ — ce qu'on a tranché, et pourquoi

Une décision par fichier, `NNNN-titre-court.md`, numérotée dans l'ordre. Elle naît d'une étude
(issue `etude`) et arrive dans la PR qui la ferme. On ne rouvre pas une décision sans une nouvelle
mesure ou un fait nouveau : on écrit alors une décision qui la remplace, et l'ancienne le dit.

## Le format

```markdown
# NNNN · Titre : ce qu'on a choisi

**Statut : adoptée.**  (proposée, adoptée, remplacée par NNNN)
**Étude :** #n

**Contexte.** Le problème, en quelques phrases, et ce qui contraint le choix.

**Options étudiées.** Une ligne par option : ce qu'elle apporte, ce qu'elle coûte, avec les liens
(fiche technique, pilote, carte du commerce).

**Décision.** Ce qu'on fait.

**Conséquences.** Ce que ça impose ailleurs : le cahier des charges, une autre étude, namfoop.

**Ce qui la rouvrirait.** La mesure ou le fait qui ferait changer d'avis.
```

Court : une décision tient sur un écran. Une mesure donne la révision de la carte, le banc et la
date, et **remplace** la précédente au lieu de s'empiler.

## Les décisions

Aucune pour l'instant : les études ouvertes sont listées dans l'épique de cadrage (#3).
