# Project IronNAS

Infrastructure de stockage réseau robuste, durcie et orientée serveur d'entreprise sur station de travail dédiée.

---

## 📌 Présentation

**IronNAS** est un projet d'infrastructure système complet conçu pour fournir une solution de stockage massif (NAS), de gestion de parc, d'authentification centralisée et de services applicatifs d'entreprise, sans recourir à des systèmes prêts à l'emploi (pas de TrueNAS, pas de ZFS).

Le projet repose sur une distribution **Debian GNU/Linux** exploitant directement les briques natives du noyau Linux (`mdadm`, LVM2, ext4) couplées à une couche applicative isolée via **Docker** et accélérée matériellement par GPU.

---

## ⚙️ Architecture Matérielle (Hardware)

* **Châssis & Carte Mère :** HP Z4 G4 Workstation
* **Processeur :** Intel Xeon W-2235 (6 cœurs / 12 threads @ 4,6 GHz)
* **Mémoire Vive :** 32 Go DDR4 ECC
* **Carte Graphique / Calcul :** NVIDIA Quadro RTX 4000 (8 Go GDDR6, Turing, transcodage NVENC/NVDEC)
* **Stockage Système (OS) :** 2x SSD M.2 NVMe en RAID 1 logiciel (`mdadm`)
* **Stockage Données :** 4x Disques durs 3,5" 2 To CMR en RAID 5 logiciel (`mdadm`)
* **Intégration Châssis :** Kit berceau baie 5,25" vers double 3,5" ventilé + câblage alimentation SATA propriétaire HP

---

## 🧱 Stack Système & Stockage

* **OS :** Debian GNU/Linux (installation minimale sans environnement de bureau)
* **Gestion RAID :** `mdadm` (RAID 5 de 4 disques 2 To $\rightarrow$ ~6 To utiles)
* **Gestion des Volumes :** LVM2 (Volume Group `vg_storage` découpé en Logical Volumes)
* **Système de Fichiers :** `ext4` avec journalisation ordonnée et options adaptées aux bandes RAID (`stride`, `stripe-width`)
* **Santé & Sondes :** `smartmontools` (`smartd`), Scrutiny, `nvme-cli`, `lm-sensors`
* **Partages Réseau :** Samba (SMBv3 durci, chiffrement forcé), NFSv4 Kernel Server

---

## 🚀 Services Applicatifs & Écosystème

L'ensemble des services additionnels est déployé via conteneurs Docker :

* **Identité & Accès :** Keycloak (SSO / OIDC), Samba 4 AD DC / OpenLDAP,...
* **Gestion de Parc :** GLPI + Agent, OPSI / WAPT, MeshCentral,,....
* **Collaboration & GED :** Nextcloud Hub, OnlyOffice Docs, Mailcow, Paperless-ngx,....
* **Supervision & Métriques :** Cockpit (`cockpit-storaged`), Uptime Kuma, Scrutiny, Prometheus + Grafana, Loki,....
* **Multimédia & IA :** Jellyfin, Immich (avec accélération GPU NVIDIA via NVIDIA Container Toolkit),....
* **Sécurité & Périmètre :** CrowdSec, Fail2ban, WireGuard, Nginx Proxy Manager, Vaultwarden,...

---

## 📂 Organisation du Dépôt

```text
├── docs/                # Spécifications, schémas d'architecture et procédures
├── scripts/             # Scripts d'automatisation, configuration mdadm, crons
├── docker/              # Fichiers docker-compose.yml par brique de service
├── licensing/           # Conditions d'utilisation, TOS et textes de licences
│   ├── LICENSE-CODE     # Licence MIT pour les scripts et configurations
│   ├── LICENSE-DOCS     # Licence CC BY-NC-SA 4.0 pour la documentation
│   ├── TERMS_OF_SERVICE.md
│   └── CREDITS.md
└── README.md

# Licences applicables au projet IronNAS

Ce projet applique une politique de double licence (**Dual-Licensing**) selon la nature des fichiers :

### 1. Code source, Scripts & Configurations (`scripts/`, `docker/`)
L'ensemble des scripts shell, playbooks, automatisations et manifestes d'orchestration est distribué sous licence **GNU Affero General Public License v3.0 (AGPLv3)**.
* Texte complet : [`licensing/LICENSE-CODE.md`](./licensing/LICENSE-CODE.md)

### 2. Documentation, Architecture & Schémas (`docs/`, `README.md`)
L'ensemble des documents textuels, fiches de spécifications, guides d'installation et schémas d'architecture est distribué sous licence **Creative Commons Attribution - Pas d'Utilisation Commerciale - Partage dans les Mêmes Conditions 4.0 International (CC BY-NC-SA 4.0)**.
* Texte complet : [`licensing/LICENSE-DOCS.md`](./licensing/LICENSE-DOCS.md)

Pour toute demande d'exploitation commerciale ou dérogation, contactez directement l'auteur.
