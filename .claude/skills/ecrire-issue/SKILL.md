---
name: ecrire-issue
description: Créer, réécrire ou cadrer une issue de namfoop-hat (épique, étude, story, chore, bug) dans le style de la backlog, lisible par un bassiste, avec le cadrage technique en commentaire. Utiliser dès qu'il faut ouvrir une issue, ou creuser et trancher une étude avec l'utilisateur.
---

# Écrire ou cadrer une issue

La référence est [`docs/style-issues.md`](../../../docs/style-issues.md) : la lire en entier avant
d'écrire.

## Écrire une issue

1. **Choisir le type** : `etude` s'il faut décider avant de dessiner, `story` si le bassiste verra
   le résultat sur la carte, `chore` pour l'atelier, `bug` pour un comportement incorrect, `epic`
   seulement pour un grand résultat que l'utilisateur a nommé. Ajouter un domaine.
2. **Chercher l'épique** : `gh issue list --label epic`. L'issue s'y rattache dans `## Liens`, et
   l'épique gagne une case.
3. **Écrire deux fichiers** hors du dépôt : le corps, aux rubriques du type, sans référence de
   composant ni nom de signal ; et le cadrage technique (`## Cadrage technique` : pistes,
   composants, pilotes, liens vers les fiches techniques, mesures à faire).
4. **Créer** l'issue avec le corps, puis poster le cadrage en commentaire.

## Cadrer une étude

1. Lire le corps, le cadrage technique et tous les commentaires.
2. Chercher : fiches techniques (lien, jamais de PDF versionné), pilotes du noyau du Pi, cartes du
   commerce qui ont résolu la même question, contraintes de namfoop (son `docs/guide.md`, ses
   ADR). Ce qu'on trouve s'ajoute en commentaire, sourcé, en séparant le vérifié du supposé.
3. Poser à l'utilisateur les questions de « À trancher », peu à la fois, chacune avec une réponse
   proposée et ce qu'elle implique. **Ne pas trancher seul.**
4. Pour chaque réponse : cocher la case, l'écrire dans une décision de `docs/decisions/` (format
   dans son `README.md`) et dans `docs/cahier-des-charges.md`.
5. Une question nouvelle devient une étude rattachée à l'épique.
6. La PR « Closes #n » livre la décision et le cahier des charges ; cocher la case de l'épique et
   mettre à jour son « Où on en est » et ses « Décisions déjà prises ».

## Le test de relecture

Un bassiste qui ne lit pas un schéma comprend-il le titre, sait-il pourquoi la question compte, et
saura-t-il dire quand elle est tranchée ? Si une phrase demande d'ouvrir une fiche technique, elle
va dans le cadrage.
