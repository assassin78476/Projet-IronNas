# Politique de Sécurité — IronNAS

## 1. Versions Supportées

Seule la version principale active sur la branche `main` bénéficie de correctifs de sécurité réguliers.

| Version | Prise en charge |
| :--- | :--- |
| `main` (dernière version) | :white_check_mark: |
| Anciennes versions / tags | :x: |

---

## 2. Signalement d'une Vulnérabilité

Si tu découvres une faille de sécurité dans un script, un template Docker Compose ou une recommandation d'architecture :

* **Ne crée pas d'Issue publique.**
* Utilise le formulaire privé de signalement : **GitHub Security Advisories** (onglet *Security* > *Advisories* > *Report a vulnerability*).
* Si indisponible, contacte directement le mainteneur par le biais de son profil GitHub.

### Informations utiles à inclure :
* Type de vulnérabilité (ex. élévation de privilèges, fuite d'identifiants, injection de commande dans un script Bash) ;
* Composant ou script concerné ;
* Étapes détaillées pour reproduire le problème (Proof of Concept) ;
* Impact potentiel sur l'hôte Debian ou les données.

---

## 3. Délais de Prise en Charge

* **Accusé de réception :** sous 48 à 72 heures ouvrées.
* **Analyse et triage :** évaluation de la gravité et isolement du composant.
* **Publication du correctif :** mise à disposition via un commit de correction sur `main` dès validation.
