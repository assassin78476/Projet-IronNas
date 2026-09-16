# Guide de Contribution — IronNAS

Merci de t'intéresser au projet IronNAS. Pour maintenir une documentation propre, des scripts fiables et un respect strict des règles du projet, merci de suivre ces directives avant toute proposition.

---

## 1. Respect des Licences & Propriété Intellectuelle

En soumettant du code ou de la documentation à ce dépôt :
* Tu acceptes que tes modifications de scripts ou de code soient publiées sous licence **GNU AGPLv3**.
* Tu acceptes que tes contributions documentaires ou schémas soient publiés sous licence **CC BY-NC-SA 4.0**.
* Tu certifies que tes contributions n'enfreignent aucun brevet ni droit d'auteur tiers.

---

## 2. Règles sur les Scripts Bash & Docker

* **Bash strict :** Tout script d'automatisation doit comporter la directive `set -euo pipefail` en en-tête.
* **En-têtes obligatoires :** Mentionne l'identifiant de licence SPDX au sommet de chaque fichier (`# SPDX-License-Identifier: AGPL-3.0-or-later`).
* **Sécurité des conteneurs :** Ne soumets aucun fichier Docker Compose exécutant des processus en `root` sur l'hôte sans isolation de privilèges (`no-new-privileges:true`).

---

## 3. Comment Proposer une Amélioration

1. Ouvre d'abord une **Issue** pour discuter de la modification envisagée (évite de développer une grosse brique logicielle si elle ne correspond pas à la feuille de route du projet).
2. Crée une branche dédiée pour ta modification :
   ```bash
   git checkout -b feature/nom-de-ta-fonctionnalite
