# Investigation SOC & Réponse à Incident (Environnement OIV)

![Wazuh](https://img.shields.io/badge/SIEM-Wazuh-00AEE0?style=for-the-badge&logo=wazuh&logoColor=white)
![MITRE](https://img.shields.io/badge/Framework-MITRE_ATT%26CK-FF6600?style=for-the-badge)
![Linux](https://img.shields.io/badge/OS-Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Raspberry Pi](https://img.shields.io/badge/Hardware-Raspberry_Pi-C51A4A?style=for-the-badge&logo=Raspberry-Pi)
![Blue Team](https://img.shields.io/badge/Role-Blue_Team-005571?style=for-the-badge)

> **Portfolio Professionnel - Analyste SOC / Blue Team**
> Simulation d'une attaque (Brute Force SSH) sur une infrastructure critique, analyse des logs via SIEM Wazuh, et rédaction de rapports d'incident professionnels.

## Contexte de l'Investigation
Ce projet documente une analyse d'incident de sécurité pour un Opérateur d'Importance Vitale (OIV) fictif. En tant qu'Analyste SOC, mon rôle a été d'étudier les alertes remontées par notre SIEM (Wazuh), d'identifier les vecteurs de compromission, et de fournir une réponse documentée.

Ce dépôt met en avant mes compétences opérationnelles en :
- Détection d'anomalies et analyse de logs (`auth.log`, alertes Wazuh).
- Qualification d'incident et triage d'alertes.
- Correspondance des tactiques avec le framework **MITRE ATT&CK**.
- Communication professionnelle (Rapport d'incident de niveau entreprise).

## Phase d'Analyse (Blue Team)

1. **Détection** : Identification d'une activité anormale sur un serveur critique (Raspberry Pi / ARM64) remontée par l'agent Wazuh.
2. **Investigation** : 
   - Analyse des règles déclenchées (ex: `5760` - SSH Insecure connection attempt, `5715` - SSH Authentication success).
   - Mapping MITRE ATT&CK (*T1110 - Brute Force*, *T1078 - Valid Accounts*).
3. **Réponse à Incident** : Rédaction d'un rapport d'incident exécutif et technique.

## Structure du Dépôt

Ce dossier se concentre sur les **livrables d'analyse et de gestion de crise** :

```bash
.
├── Livrables/                 
│   ├── rapport-d'incident.md         # Synthèse de l'incident et actions de remédiation
│   ├── rapport-incident-detail.md    # Analyse technique détaillée (Logs, MITRE)
│   └── fluxEnergie-simulation.md     # Contexte métier de l'OIV
└── README.md
```

## Objectif Carrière
Ce projet a été réalisé dans le cadre de ma recherche d'alternance en tant qu'**Analyste SOC Junior / Analyste Cybersécurité**. Il valide ma capacité à analyser des comportements suspects et à documenter de manière claire, concise et professionnelle un incident de sécurité, des compétences essentielles au sein d'une Blue Team.

---
*Les rapports présentés dans ce dépôt résultent d'une simulation contrôlée (Home Lab).*