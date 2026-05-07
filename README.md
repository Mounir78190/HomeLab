# 🔐 HomeLab Sécurisé — Cybersecurity Lab

Infrastructure réseau sécurisée conçue dans le cadre de ma formation RNCP Opérateur en Cybersécurité à l’EECS.

Ce projet reproduit une architecture proche d’un environnement professionnel afin de mettre en pratique des compétences en :

- Segmentation réseau
- Administration système
- Sécurisation d’infrastructure
- Supervision & détection
- Analyse de vulnérabilités
- Tests offensifs contrôlés

> ⚠️ Toutes les informations sensibles (IP publiques, MAC Address, accès WAN, clés VPN) ont été anonymisées.

---

# 🎯 Objectifs du projet

Ce HomeLab a été conçu afin de :

- Déployer une infrastructure segmentée par VLAN
- Mettre en place un pare-feu centralisé pfSense
- Contrôler les flux réseau inter-VLAN
- Simuler des scénarios d’attaque réalistes
- Détecter des comportements suspects via CrowdSec
- Renforcer l’administration distante avec WireGuard VPN
- Appliquer les principes de défense en profondeur

---

# 🏗️ Architecture Réseau

## Segmentation VLAN

| VLAN | Nom | Rôle |
|---|---|---|
| VLAN 10 | ADMIN | Administration & supervision |
| VLAN 20 | DEV | Environnement Windows / services |
| VLAN 30 | HACKETH | Machine offensive Kali Linux |

---

# ⚙️ Technologies utilisées

## Réseau & Sécurité
- pfSense
- CrowdSec
- WireGuard VPN
- TP-Link Omada (802.1Q)
- VLAN
- NAT
- Firewall Rules

## Systèmes
- Ubuntu
- Windows 11 Pro
- Kali Linux

## Outils sécurité
- Nmap
- Hydra
- Wireshark
- Metasploit

## Services
- CUPS
- SSH
- HTTP/HTTPS

---

# 🛡️ Fonctionnalités de sécurité

## 🔥 pfSense

Le pare-feu pfSense constitue le cœur de l’architecture :

- Routage inter-VLAN
- Filtrage réseau
- NAT
- Contrôle WAN
- Journalisation

---

## 👁️ CrowdSec

Intégration de CrowdSec directement sur pfSense :

- Détection comportementale
- Analyse des logs
- Détection bruteforce
- Blocage dynamique des IP malveillantes

---

## 🔐 VPN WireGuard

Mise en place d’un accès distant sécurisé via WireGuard :

- Tunnel VPN chiffré
- Accès distant au VLAN ADMIN
- Administration sécurisée hors WAN public
- Authentification par clés
- Réduction de la surface d’exposition

---

# 🧪 Scénarios d’attaque réalisés

## 🔍 Reconnaissance réseau

```bash
nmap -sS IP
```

### Objectif
- Découverte d’hôtes
- Identification des ports ouverts
- Vérification de la segmentation réseau

### Résultat
- Détection des services exposés
- Analyse des flux autorisés
- Détection des comportements suspects par CrowdSec

---

## ⚠️ Scan de vulnérabilités

```bash
nmap --script vuln IP
```

### Objectif
- Recherche de vulnérabilités connues
- Analyse des services actifs
- Évaluation de la surface d’attaque

### Résultat
- Identification des services accessibles
- Détection des failles potentielles
- Validation du cloisonnement réseau

---

## 🚫 Tentative d’accès non autorisé

```bash
nmap -p 22,80,631,9922 IP
```

### Objectif
- Tester l’exposition des services sensibles
- Vérifier les règles firewall
- Contrôler l’accès inter-VLAN

### Résultat
- SSH bloqué
- HTTP bloqué
- Services non autorisés filtrés
- Seuls les flux explicitement autorisés restent accessibles

---

## ↔️ Tentative de mouvement latéral

```bash
nmap -sV IP
```

### Objectif
- Vérifier l’isolation réseau
- Tester les restrictions inter-VLAN
- Contrôler l’exposition des services Windows

### Résultat
- Segmentation efficace
- Limitation des mouvements latéraux
- Services sensibles non exposés

---

## 🔓 Simulation d’attaque Bruteforce

```bash
hydra -l admin -P rockyou.txt ssh://IP
```

### Objectif
- Simuler une attaque par dictionnaire
- Observer le comportement défensif
- Tester les mécanismes de détection

### Protection observée
- Blocage SSHGuard
- Détection CrowdSec
- Limitation des tentatives
- Réduction du risque de compromission

---

# 📊 Principes de sécurité appliqués

- Principe du moindre privilège
- Défense en profondeur
- Segmentation réseau
- Contrôle des flux
- Journalisation des événements
- Détection comportementale
- Réduction des mouvements latéraux

---

# 🌐 Mise en place du VPN WireGuard

## 🎯 Objectifs

- Sécuriser l’accès distant
- Éviter toute administration depuis Internet sans VPN
- Chiffrer les communications
- Centraliser l’accès administratif

---

## ⚙️ Fonctionnement

- WireGuard est déployé sur pfSense
- Les clients VPN reçoivent une IP dédiée
- Seul le VLAN ADMIN est accessible via le tunnel
- Les accès WAN directs sont bloqués

---

## 🔐 Sécurité

- Authentification par clés
- Chiffrement moderne
- Réduction de l’exposition des services internes
- Administration distante sécurisée

---

# 📈 Évolutions prévues

- Déploiement SIEM (Splunk / Wazuh)
- Centralisation des logs
- Reverse Proxy sécurisé
- Supervision avancée
- Active Directory
- Détection & corrélation d’événements
- Dashboard SOC

---

# 🧠 Compétences développées

## 🔵 Blue Team

- Supervision
- Analyse de logs
- Détection d’attaques
- Segmentation réseau
- Analyse comportementale

---

## 🌐 Réseau

- VLAN
- Routage
- NAT
- Firewall
- Contrôle d’accès

---

## ⚔️ Offensive Security

- Scan réseau
- Analyse de vulnérabilités
- Bruteforce contrôlé
- Validation des protections

---

## 🖥️ Administration

- Linux
- Windows
- Services réseau
- VPN
- pfSense

---

# 📸 Aperçu du Lab

## 🏗️ Architecture du HomeLab

![Architecture réseau](/Home_Lab.drawio_git.png)

---

## 🔥 Configuration des interfaces pfSense

![Interfaces pfSense](/pfsense_git.png)

---

## 🌐 Configuration VLAN sur TP-Link Omada

![VLAN Omada](/tp_link_git.png)

---

## 👁️ Supervision CrowdSec

![CrowdSec](/Crowdsec_git.png)

---

## 🔍 Scan réseau depuis Kali Linux

![Nmap Scan](/Nmap1_git.png)

---

## 🚫 Tentative d’accès non autorisé

![Unauthorized Access](/Nmap2_git.png)

---

## ↔️ Test de mouvement latéral

![Lateral Movement](/Nmap3_git.png)

---

## 🔐 VPN WireGuard sur pfSense

![WireGuard](/Wireguard_git.png)

---

# 📚 Contexte pédagogique

Projet réalisé dans le cadre du titre RNCP Opérateur en Cybersécurité à l’EECS.

L’objectif est de développer une approche :
- Défensive
- Offensive
- Opérationnelle

à travers un environnement d’expérimentation réaliste.

---

# 👨‍💻 Auteur

**Mounir KOUSKOUS**  
Opérateur Cybersécurité | SOC Junior | Administrateur Système & Réseau

📍 France  
🔗 LinkedIn :  
https://www.linkedin.com/in/mounir-kouskous/
