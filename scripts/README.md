<!--
SPDX-License-Identifier: CC-BY-SA-4.0
SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
-->

# scripts/ — un script par geste

Sous **GPL-3.0-or-later**. Règles, comme dans namfoop-install :

- Bash, `set -euo pipefail`, `shellcheck` sans avertissement (la CI le vérifie).
- En tête, après le shebang :

  <!-- REUSE-IgnoreStart -->
  ```sh
  # SPDX-License-Identifier: GPL-3.0-or-later
  # SPDX-FileCopyrightText: © 2026 les auteurs de namfoop-hat (AUTHORS.md)
  ```
  <!-- REUSE-IgnoreEnd -->
- Idempotents : relancer ne change rien. Ce qui écrit sur une carte (flasher l'EEPROM) demande
  confirmation et a un `--dry-run`.
- Messages en français.
