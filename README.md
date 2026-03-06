# microsoft-sentinel-soc-lab
# Microsoft Sentinel SOC Investigation – SolarWinds / Solorigate Attack Simulation

## Overview

This project demonstrates a Security Operations Center (SOC) investigation performed using Microsoft Sentinel.
The investigation simulates a multi-stage cyber attack involving password spraying, account compromise, command-and-control communication, and persistence through malicious mailbox rules.

The goal of the investigation was to analyse security alerts, correlate events, enrich indicators using threat intelligence sources, and classify the alerts appropriately.

---

## Technologies Used

* Microsoft Sentinel (SIEM)
* Microsoft Defender XDR
* Azure Log Analytics
* Threat Intelligence Enrichment
* VirusTotal OSINT analysis

---

## Attack Scenario

The investigation identified a sequence of malicious activity indicating a coordinated attack.

### Stage 1 – Credential Attack (Password Spraying)

Multiple authentication attempts originated from the external IP address:

175.45.176.99

The IP attempted to sign in to several disabled accounts before successfully authenticating to the user account:

[AdeleV@contoso.onmicrosoft.com](mailto:AdeleV@contoso.onmicrosoft.com)

This behaviour is consistent with password spraying techniques used by attackers to identify valid credentials.

---

### Stage 2 – Command and Control Communication

A Sentinel alert detected network beacon activity associated with the domain:

avsvmcloud.com

Threat intelligence analysis using VirusTotal confirmed the domain is flagged by multiple vendors as malicious and associated with command-and-control infrastructure related to the SolarWinds / Solorigate attack.

---

### Stage 3 – Persistence via Mailbox Rule

Following the successful login, a malicious inbox rule was created in the compromised mailbox.

The rule attempted to hide emails containing the phrase:

"do not open"

Attackers commonly create such rules to delete or hide security notifications and maintain persistence within the compromised account.

---

## Investigation Outcome

All alerts were investigated and classified as **True Positives**, forming a **multi-stage attack chain** consisting of:

* Credential attack (password spraying)
* Successful account compromise
* Command-and-control communication
* Persistence through mailbox rule manipulation

---

## Key Skills Demonstrated

* SIEM investigation using Microsoft Sentinel
* Alert triage and classification
* Threat intelligence enrichment
* Multi-stage attack correlation
* Incident documentation
* SOC investigation workflow

---

## Screenshots

Screenshots demonstrating the investigation process are included in the repository.

---
