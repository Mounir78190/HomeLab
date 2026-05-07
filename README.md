# 🔐 HomeLab Sécurisé — Cybersecurity Lab

![pfSense](https://img.shields.io/badge/pfSense-Firewall-red)
![CrowdSec](https://img.shields.io/badge/CrowdSec-IDS%2FIPS-blue)
![WireGuard](https://img.shields.io/badge/WireGuard-VPN-orange)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-black)

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

# 🧩 Difficultés rencontrées

La mise en œuvre de cette infrastructure HomeLab m’a confronté à plusieurs problématiques techniques concrètes, proches de celles rencontrées dans des environnements professionnels. Ces difficultés ont constitué une phase d’apprentissage importante, notamment sur les mécanismes réseau, le routage et la sécurisation des flux. :contentReference[oaicite:0]{index=0}

---

## 🌐 Configuration VLAN trunk / access

L’une des principales difficultés a concerné la cohérence entre :

- la configuration logique des VLAN sur pfSense ;
- la configuration physique du switch TP-Link Omada ;
- l’adressage IP des différentes machines. 

Plusieurs anomalies ont été rencontrées :

- VLAN actifs mais sans connectivité ;
- absence de communication entre certaines machines ;
- erreurs d’affectation des ports ;
- mauvaise compréhension initiale entre ports **TRUNK** et **ACCESS**.

La résolution du problème a nécessité :

- la reconfiguration du port trunk entre le switch et pfSense ;
- la vérification de l’encapsulation 802.1Q ;
- des tests réseau via `ping`, `arp` et analyse des tables ARP. 

Cette étape m’a permis de mieux comprendre :

- la segmentation réseau couche 2 ;
- le fonctionnement des VLAN ;
- la gestion des communications inter-segments.

---

## 🔀 Routage inter-VLAN

Le routage inter-VLAN a représenté une autre difficulté importante du projet.

Malgré une configuration réseau apparemment correcte, certaines machines ne pouvaient pas :

- joindre leur passerelle ;
- communiquer avec d’autres VLAN ;
- accéder à Internet. 

Les investigations ont mis en évidence :

- des routes incorrectes ;
- des interfaces mal configurées ;
- des incohérences dans les passerelles ;
- des règles firewall trop restrictives. 

Pour résoudre ces problèmes, plusieurs outils de diagnostic ont été utilisés :

```bash
ping
ip route
arp -a
nslookup
```

L’analyse progressive des flux réseau et des logs pfSense a permis de valider la matrice de flux définie lors de la conception de l’architecture. 

---

## 🔥 NAT et connectivité WAN via passerelle Linux

La connectivité WAN a constitué une difficulté particulière.

pfSense ne disposant pas d’interface Wi-Fi, il était impossible de connecter directement le pare-feu au réseau domestique sans équipement intermédiaire. 

Pour contourner cette contrainte, une machine Linux a été configurée comme passerelle :

- interface Wi-Fi connectée à Internet ;
- interface Ethernet reliée au WAN pfSense ;
- partage de connexion via routage IP et NAT. 

Plusieurs problèmes ont été rencontrés :

- absence d’accès Internet depuis pfSense ;
- erreurs de routage ;
- configuration NAT incomplète ;
- incohérences de passerelle. }

La résolution a nécessité :

- l’activation du routage IP ;
- la configuration du NAT sur la machine Linux ;
- la vérification des routes et passerelles ;
- des tests de connectivité WAN. 

Cette phase m’a permis de mieux comprendre :

- le fonctionnement du NAT ;
- la translation d’adresses ;
- les mécanismes de partage de connexion ;
- le rôle des passerelles réseau.

---

## 👁️ Détection CrowdSec

L’intégration de CrowdSec sur pfSense a également nécessité plusieurs phases de tests et d’ajustement.

L’objectif était de :

- détecter les scans réseau ;
- identifier les tentatives de bruteforce ;
- analyser les comportements suspects ;
- automatiser le blocage des IP malveillantes. 

L’installation a été réalisée directement depuis le shell pfSense via le dépôt officiel CrowdSec :

```bash
git clone https://github.com/crowdsecurity/pfSense-pkg-crowdsec.git
sh install-crowdsec.sh
```

Plusieurs points ont nécessité une attention particulière :

- validation des log processors ;
- intégration avec les logs pfSense ;
- vérification des remédiations automatiques ;
- interprétation des alertes CrowdSec. 

Lors des simulations d’attaque par bruteforce avec Hydra, certaines attaques étaient bloquées directement par `sshguard`, empêchant CrowdSec de générer des alertes exploitables. Cette situation a permis de mieux comprendre l’interaction entre :

- protections locales ;
- firewall ;
- mécanismes IDS/IPS ;
- journalisation des événements. 

---

## 🛡️ Gestion des règles firewall

La mise en place des règles firewall sur pfSense a demandé plusieurs ajustements afin d’appliquer correctement le principe du moindre privilège.

Les objectifs étaient :

- autoriser uniquement les flux nécessaires ;
- limiter les mouvements latéraux ;
- protéger le VLAN ADMIN ;
- empêcher l’exposition inutile des services sensibles. 

Plusieurs difficultés ont été rencontrées :

- règles trop permissives ;
- blocages involontaires ;
- conflits entre NAT et firewall ;
- mauvaise priorisation des règles. 

La validation s’est faite via :

- des scans Nmap ;
- des tests de connectivité ;
- l’analyse des logs pfSense ;
- des simulations d’attaque contrôlées depuis Kali Linux. 

Cette étape a renforcé ma compréhension :

- des politiques de filtrage ;
- des flux réseau ;
- du contrôle d’accès ;
- de la défense en profondeur.

---

## 🧠 Enseignements tirés du projet

Ces différentes difficultés ont constitué une expérience très formatrice.

Elles m’ont permis de développer des compétences concrètes en :

- troubleshooting réseau ;
- segmentation VLAN ;
- routage et NAT ;
- administration pfSense ;
- analyse des flux réseau ;
- détection comportementale ;
- sécurisation d’infrastructures. 

Ce projet m’a également permis de mieux comprendre l’importance :

- d’une architecture cohérente ;
- de la supervision ;
- de la journalisation ;
- et de l’analyse des comportements réseau dans une logique SOC et cybersécurité opérationnelle.

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
