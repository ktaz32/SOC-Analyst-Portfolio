# SOC Knowledge Base

This directory contains operational reference material that supports the investigations in this portfolio.

The goal is not to reproduce course notes. Each reference is written around practical SOC questions:

- What telemetry matters?
- What behavior is normal?
- What makes an event suspicious?
- What evidence would confirm the activity?
- What cannot be concluded from the available data?
- How should the behavior be mapped to MITRE ATT&CK?
- What detection opportunities follow from the investigation?

---

# Current Knowledge References

| Topic | Location | Practical Focus |
|---|---|---|
| Cyber Kill Chain | [`cyber-kill-chain/`](./cyber-kill-chain/) | Investigation pivots across attack stages |
| MITRE ATT&CK | [`MITRE-ATT&CK/`](./MITRE-ATT&CK/) | Evidence-based tactics/techniques/sub-techniques mapping |
| Phishing Email Analysis | [`Phishing-email-analysis/`](./Phishing-email-analysis/) | Headers, sender validation, URLs, attachments, delivery impact |
| Detecting Web Attacks | [`detecting-web-attacks/`](./detecting-web-attacks/) | HTTP, SQLi, XSS, IDOR, LFI, response analysis |
| Detecting Web Attacks 2 | [`detecting-web-attacks-2/`](./detecting-web-attacks-2/) | Brute force, traversal, open redirect, XXE, defensive patterns |
| SIEM 101 | [`siem-101/`](./siem-101/) | Log aggregation, parsing, normalization, storage, alerting |
| SIEM Alert Investigation | [`siem-alert-investigation/`](./siem-alert-investigation/) | Triage, evidence pivots, scoping, verdict, closure |
| Incident Management 101 | [`incident-management-101/`](./incident-management-101/) | Case management, playbooks, SIEM/SOAR/CTI workflow |
| Network Log Analysis | [`network-log-analysis/`](./network-log-analysis/) | Netflow, WAF, SMTP, protocol and traffic analysis |
| Security Solutions | [`security-solutions/`](./security-solutions/) | IDS/IPS, firewalls, endpoint protection, WAF, sandboxing |
| Malware Analysis Fundamentals | [`malware-analysis-fundamentals/`](./malware-analysis-fundamentals/) | Static/dynamic analysis, sandboxing, processes, persistence, network behavior |
| Dynamic Malware Analysis | [`dynamic-malware-analysis/`](./dynamic-malware-analysis/) | Process Hacker, Procmon, Regshot, Wireshark, Fiddler, persistence |
| Malicious Document Analysis | [`malicious-document-analysis/`](./malicious-document-analysis/) | Office documents, macros, deobfuscation, downloader behavior |
| Splunk | [`splunk/`](./splunk/) | Windows log ingestion, indexes, search, fields, reports, dashboards, RBAC |
| Cyber Threat Intelligence | [`cyber-threat-intelligence/`](./cyber-threat-intelligence/) | CTI lifecycle, IOC validation, attack surface, EASM/DRP, SOC integration |
| VirusTotal for SOC Analysts | [`virustotal-soc-analyst/`](./virustotal-soc-analyst/) | Detection, Details, Relations, Behavior, freshness, correlation |
| Detecting Brute Force Attacks | [`brute-force-attack-detection/`](./brute-force-attack-detection/) | SSH/HTTP/RDP brute force, Windows 4624/4625 correlation, prevention |

**Current total: 17 operational references.**

---

# Core Analyst Principles

## Evidence Before Conclusion

A detection rule, IOC reputation result, or automated sandbox verdict is the beginning of analysis.

Where possible, correlate:

```text
Alert
 + SIEM logs
 + Endpoint telemetry
 + Network activity
 + Sandbox behavior
 + Threat intelligence
 + User / host context
```

## Evidence vs Inference

### Direct Evidence
What logs or artifacts explicitly show.

### Analyst Inference
What can reasonably be concluded.

### Not Established
What cannot be proven.

This distinction prevents unsupported claims about exploitation success, malware execution, C2, persistence, credential compromise, lateral movement, or exfiltration.

## Detection Is Not Compromise

```text
SQLi payload observed ≠ database compromise confirmed
malicious attachment delivered ≠ malware execution confirmed
outbound connection observed ≠ C2 automatically confirmed
SMTP session observed ≠ data exfiltration automatically confirmed
4625 failures followed by 4624 ≠ brute-force success until account/source context is correlated
```

---

# Current Practical Coverage

## SIEM / Log Analysis

- log aggregation, parsing, normalization, enrichment, storage, and alerting
- SIEM investigation workflow
- Splunk indexes, ingestion, forwarders, search modes, fields, reports, and dashboards
- Windows Security events
- Event IDs 4624 and 4625
- authentication correlation

## Network / Web

- HTTP fundamentals and web-server logs
- WAF and firewall telemetry
- NetFlow concepts
- SMTP analysis
- SQL injection, XSS, IDOR, LFI, directory traversal, command injection
- brute-force and login analysis

## Malware / Documents

- static vs dynamic analysis
- malicious Office documents and VBA/macros
- VirusTotal Detection / Details / Relations / Behavior
- sandbox behavior
- process trees and short-lived child processes
- Procmon filtering
- `%TEMP%`, `%APPDATA%`, Startup locations
- Run / RunOnce persistence
- scheduled tasks and WMI
- Process Hacker, Regshot, Wireshark, Fiddler
- DNS / HTTP / SMTP behavior
- dropped payloads and ransomware behavior

## Threat Intelligence / Incident Handling

- CTI lifecycle
- technical, tactical, operational, and strategic intelligence
- IOC validation and freshness
- attack-surface intelligence
- EASM / DRP concepts
- SIEM / SOAR / EDR / firewall CTI integration
- incident-management workflow and playbooks

---

# Detection Engineering Mindset

The knowledge material is used to derive detection hypotheses.

Examples:

```text
Office process
+
unexpected child process
+
outbound network connection
```

```text
unknown executable
+
AppData file creation
+
Run-key modification
+
outbound SMTP
```

```text
repeated Event ID 4625
+
same account/source context
+
subsequent Event ID 4624
```

Strong detections should consider expected baselines, false positives, process ancestry, time windows, telemetry quality, negative test cases, and tuning boundaries.

---

# Current Topics

- SOC fundamentals
- Cyber Kill Chain
- MITRE ATT&CK
- phishing / email
- SIEM fundamentals
- Splunk
- incident management
- CTI
- VirusTotal
- network logs
- IDS / IPS / firewalls / WAF
- HTTP and web attacks
- brute-force / authentication attacks
- malware-analysis fundamentals
- dynamic malware analysis
- malicious-document analysis
- process / file / registry / network behavior
- persistence
- IOC enrichment
- detection engineering

---

# Future Expansion

Planned deeper areas include:

- Sysmon
- PowerShell Script Block logging
- Active Directory
- Kerberos / NTLM authentication analysis
- advanced Splunk SPL
- threat hunting
- Sigma correlation engineering
- YARA
- memory forensics
- disk forensics

---

# Purpose

The knowledge base supports the portfolio workflow:

**Understand → Detect → Investigate → Validate → Scope → Respond → Improve**

The emphasis remains on practical analyst reasoning and evidence interpretation.
