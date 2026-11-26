<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: 2026 les contributeurs de namfoop-hat
-->

# firmware/ — ce qui fait reconnaître la carte

Sous **GPL-3.0-or-later**, comme namfoop. Chaque fichier source commence par :

<!-- REUSE-IgnoreStart -->
```
SPDX-License-Identifier: GPL-3.0-or-later
SPDX-FileCopyrightText: 2026 les contributeurs de namfoop-hat
```
<!-- REUSE-IgnoreEnd -->

(en commentaire `//` ou `/* */` pour un overlay device tree.)

On y range ce que le Pi 5 lit pour savoir quelle carte est branchée et comment lui parler :

```
firmware/
  overlay/   l'overlay device tree (.dts) qui déclare la carte son au noyau
  eeprom/    le contenu de l'EEPROM d'identification de la carte (spécification HAT+)
```

Les binaires compilés (`.dtbo`, image d'EEPROM) ne sont pas versionnés : `scripts/` les produit.
Une carte vendue avec son EEPROM programmée donne aussi la source de ce qu'elle contient (GPL) :
ce dossier, au tag de la révision.
