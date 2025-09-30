# SOC-Automation-with-SOAR-SOC-Automation-with-SOAR-
This project shows how a SOC can automate repetitive tasks using SOAR tools. It implements workflows to check IP reputation, block malicious IPs, perform malware hash lookups, and create cases in TheHive—improving response speed and reducing human error in SOC operations.
SOC Automation with SOAR (Shuffle + TheHive + Cortex)
🔹 Overview

This project demonstrates how a Security Operations Center (SOC) can automate security tasks using SOAR (Security Orchestration, Automation, and Response) tools.
It integrates Shuffle, TheHive, and Cortex to automatically:

Check IP/malware reputation

Block malicious IPs

Generate incident tickets in TheHive

Notify SOC analysts

🔹 Features

Automated IP reputation checks via VirusTotal and AbuseIPDB

Workflow-based firewall/EDR blocking for malicious IPs

Automatic incident creation in TheHive

Email/Slack alerts to SOC team

Easy to extend for additional analyzers and workflows

🔹 Tools & Technologies

Shuffle – SOAR orchestration platform

TheHive – Incident response and case management

Cortex – Threat intelligence analyzer

VirusTotal & AbuseIPDB APIs – Threat intelligence sources

Docker & Docker Compose – Lab setup and deployment

🔹 Architecture
              ┌───────────────┐
              │   SIEM/Logs   │
              │ (Splunk/ELK)  │
              └──────┬────────┘
                     │ Suspicious IP / Hash
                     ▼
          ┌────────────────────┐
          │   Shuffle (SOAR)   │
          │  Orchestration Hub │
          └───────┬────────────┘
                  │
   ┌──────────────┼──────────────┐
   ▼              ▼              ▼
┌───────┐   ┌───────────┐   ┌─────────────┐
│Cortex │   │TheHive IR │   │ Firewall/EDR │
│Analyzers│ │Ticket Mgmt│   │ Auto-block   │
└───────┘   └───────────┘   └─────────────┘

🔹 Setup Instructions

Install Docker & Docker Compose

Run Shuffle:

docker run -d -p 3001:3001 frikky/shuffle:latest


Run TheHive & Cortex using Docker Compose:

docker-compose up -d


Configure Cortex analyzers with API keys (VirusTotal, AbuseIPDB).

Import workflow JSON in Shuffle.

Run workflow with a test IP or malware hash.

🔹 Demo

Input suspicious IP in Shuffle workflow.

Cortex checks reputation → returns malicious/clean status.

Workflow blocks IP automatically (Firewall/EDR).

Incident ticket created in TheHive.

Email/Slack alert sent to SOC team.

🔹 Contribution

Fork the repo to add new analyzers or workflows

Add integration with other threat intelligence sources

Report issues or submit pull requests for improvements
