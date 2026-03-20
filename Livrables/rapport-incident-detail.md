<link rel="stylesheet" href="style.css">

## Analyse MITRE ATT&CK

### Tactiques et Techniques Identifiées

| Tactic | Technique | ID | Description |
|--------|-----------|-----|------------|
| **Initial Access** | Valid Accounts | T1078 | Utilisation de comptes valides après brute force |
| **Credential Access** | Brute Force | T1110.001 | Attaque par force brute sur authentification SSH |
| **Persistence** | Valid Accounts | T1078 | Maintien d'accès via compte compromis |

---

## Évaluation des Risques

### Impact
- **Confidentialité:** ÉLEVÉE - Accès non autorisé au système
- **Intégrité:** MOYENNE - Possibilité de modification des données
- **Disponibilité:** MOYENNE - Risque de déni de service ou sabotage

### Vecteur d'attaque
- Source: Réseau interne (192.168.1.174)
- Type: Attaque par dictionnaire/brute force
- Protocole: SSH (port 22)

---

## Actions de Réponse Immédiate

### 1. Containment (Isolement)
- [ ] Désactiver immédiatement le compte "targetadmin"
- [ ] Bloquer l'IP source 192.168.1.174 au niveau du firewall
- [ ] Isoler le système compromis (192.168.1.31) du réseau
- [ ] Révoquer toutes les sessions SSH actives

### 2. Éradication
- [ ] Changer les mots de passe des comptes "root" et "targetadmin"
- [ ] Vérifier les autres comptes système pour détecter toute compromission
- [ ] Scanner le système pour détecter backdoors, rootkits ou malwares
- [ ] Examiner les logs système pour identifier les actions post-compromission

### 3. Investigation approfondie
- [ ] Analyser les commandes exécutées par l'attaquant (historique bash, syslog)
- [ ] Vérifier les modifications de fichiers système
- [ ] Examiner les connexions réseau sortantes depuis le système compromis
- [ ] Identifier la source de l'IP 192.168.1.174 (machine compromise ou attaquant interne)

---

## Recommandations de Sécurité

### Court terme
1. **Authentification forte:**
   - Implémenter l'authentification par clés SSH uniquement
   - Désactiver l'authentification par mot de passe SSH
   - Activer l'authentification multi-facteurs (MFA) si possible

2. **Détection et prévention:**
   - Configurer Fail2ban pour bannir automatiquement les IPs après 3-5 tentatives échouées
   - Réduire le timeout de bannissement SSH
   - Activer les alertes en temps réel pour les règles 5760 et 5715

3. **Durcissement SSH:**
   - Désactiver l'accès SSH root (`PermitRootLogin no`)
   - Changer le port SSH par défaut (22 → port personnalisé)
   - Limiter les utilisateurs autorisés à se connecter via SSH (`AllowUsers`)
   - Implémenter une liste blanche d'IPs autorisées

### Moyen/Long terme
1. Implémenter un système de gestion des accès privilégiés (PAM)
2. Mettre en place une politique stricte de complexité des mots de passe
3. Effectuer des audits réguliers des comptes système
4. Déployer un honeypot SSH pour détecter les activités de scanning
5. Former les utilisateurs sur les bonnes pratiques de sécurité des mots de passe

---

## Artifacts et IOCs (Indicators of Compromise)

| Type | Valeur | Description |
|------|--------|-------------|
| IP Address | 192.168.1.174 | IP source de l'attaquant |
| Username | root | Premier compte ciblé |
| Username | targetadmin | Compte compromis |
| Port | 22 | Service SSH compromis |
| Wazuh Rule | 5760 | Authentification échouée |
| Wazuh Rule | 5715 | Authentification réussie |

---

## Leçons Apprises

1. **Absence de protection contre le brute force:** Aucun mécanisme de limitation de tentatives n'était en place
2. **Authentification faible:** Les mots de passe des comptes étaient suffisamment faibles pour être compromis
3. **Accès root SSH activé:** Le compte root était accessible via SSH, augmentant la surface d'attaque
4. **Temps de réponse:** La détection a été effectuée post-compromission, soulignant le besoin d'alertes en temps réel

---

## Conclusion

Cette attaque par brute force SSH démontre l'importance d'une configuration de sécurité SSH robuste et de mécanismes de détection/prévention actifs. L'attaquant a réussi à compromettre le compte "targetadmin" après environ 48 tentatives, ce qui indique un mot de passe faible ou prévisible.

Les mesures de remédiation doivent être appliquées immédiatement pour prévenir toute compromission future et sécuriser l'infrastructure contre ce type d'attaque.

---

**Prochaines étapes:**
1. Exécuter les actions de réponse immédiate
2. Conduire une investigation forensique complète du système compromis
3. Mettre à jour les procédures de sécurité SSH
4. Présenter les résultats lors de la prochaine réunion de l'équipe SOC
