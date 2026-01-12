# Déploiement SIEM IoT – Wazuh & Graylog avec ESP32

## Objectif du projet

Déployer une **plateforme SIEM complète** basée sur **Wazuh et Graylog**,  
et connecter un **équipement IoT (ESP32)** afin de :
- centraliser les journaux,
- superviser les événements,
- valider une chaîne de collecte IoT réaliste.

---

## Environnement

- **VM Ubuntu**
- Déploiement via **Docker & Docker Compose**
- Architecture **single-node**
- Environnement pédagogique et reproductible

---

## Déploiement avec Docker

- Installation de Docker via le script officiel
- Utilisation de Docker Compose pour :
  - Graylog
  - OpenSearch
  - MongoDB
  - Wazuh (manager, indexer, dashboard)

Avantages :
- Déploiement rapide
- Isolation des services
- Reproductibilité du lab

---

## Déploiement Graylog

### Stack Graylog
- MongoDB : métadonnées
- OpenSearch : indexation
- Graylog : visualisation & analyse

### Sécurisation
- Génération de secrets cryptographiques
- Mot de passe administrateur hashé (SHA-256)
- Configuration réseau contrôlée

### Configuration Syslog
- Création d’un input **Syslog UDP**
- Port non privilégié (1514/UDP)
- Réception des journaux IoT

---

## Déploiement Wazuh

- Installation via dépôt officiel Docker
- Génération des certificats
- Ajustement des paramètres système :
  - `vm.max_map_count`
  - désactivation du swap
- Accès sécurisé au dashboard en HTTPS

Wazuh assure :
- la centralisation des événements de sécurité
- l’analyse et la supervision

---

## Connexion ESP32 au SIEM

### ESP32 – MicroPython
- Connexion Wi-Fi
- Envoi périodique de journaux Syslog UDP
- Identification claire de la source (`ESP32-IOT-01`)

### Chaîne de collecte
ESP32 → Graylog → OpenSearch  
Wazuh → analyse complémentaire des événements

---

## Tests & validation

- Vérification de la réception des logs dans Graylog
- Visualisation en temps réel des événements
- Confirmation de l’indexation et de la persistance
- Validation de la chaîne IoT → SIEM

---

## Apports du projet

- Mise en œuvre complète d’une **plateforme SIEM**
- Supervision IoT / OT
- Compréhension des flux de logs
- Approche réaliste orientée exploitation et sécurité

---

## Conclusion

Ce projet démontre la capacité à :
- déployer une infrastructure SIEM moderne,
- intégrer des équipements IoT,
- analyser et superviser des événements de sécurité,
dans un environnement contrôlé et professionnel.
