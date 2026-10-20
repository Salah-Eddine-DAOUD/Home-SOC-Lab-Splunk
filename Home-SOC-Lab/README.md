# 🛡️ Home SOC Lab : Détection d'attaques SSH Brute-Force et Réponse aux Incidents

## 📌 Présentation du Projet

Construction d'un laboratoire SOC (Security Operations Center) fonctionnel pour simuler des cyberattaques réelles, les détecter à l'aide de Splunk SIEM et effectuer une réponse aux incidents.

## 🎥 Démonstration Vidéo

[Regarder la démonstration vidéo (Avant/Après) ici]: https://lnkd.in/p/enFkRj5F

## 🏗️ Architecture du Laboratoire

- **Windows Host :** Exécute Splunk Enterprise (SIEM) sur le port 9997.
- **Ubuntu VM :** Exécute le serveur SSH et le Splunk Universal Forwarder.
- **Kali Linux VM :** Utilisé comme machine attaquante (Attacker).

## 🚀 Fonctionnalités Clés Implémentées

1. **Collecte de Logs :** Transfert de `/var/log/auth.log` et `/var/log/syslog` d'Ubuntu vers Splunk.
2. **Simulation d'Attaques :** Exécution d'un scan Nmap, d'une attaque SSH Brute Force (30 tentatives) et d'une connexion réussie depuis Kali.
3. **Détection (SPL) :** Utilisation de `rex` pour extraire les adresses IP des attaquants et `stats` pour corréler les événements.
4. **Alertes :** Création d'une alerte Splunk pour les IP dépassant 5 tentatives échouées.
5. **Tableau de Bord :** Création d'un Dashboard en mode sombre affichant le total, les échecs, les succès et l'activité de scan de ports.
6. **Réponse aux Incidents :** Blocage de l'IP de l'attaquant à l'aide de UFW sur Ubuntu.

## 📊 Requêtes SPL Utilisées

Vous pouvez trouver toutes les requêtes SPL utilisées dans le fichier `spl_queries/queries.md`.

## 📸 Captures d'écran

- **Dashboard Avant l'attaque :** `dashboard/dashboard_before.png`
- **Dashboard Après l'attaque :** `dashboard/dashboard_after.png`
- **Blocage UFW :** `incident_response/ufw_block.txt`
