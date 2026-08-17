# SOC Analyst Portfolio

Welcome to my cybersecurity portfolio.

This repository documents my practical development as a **Security Operations Center (SOC) Analyst**, with a focus on alert triage, security investigations, incident response, threat intelligence, SIEM analysis, malware analysis, network analysis, and detection engineering.

I recently completed **CompTIA Security+** and am currently developing hands-on SOC experience through structured security labs and simulated investigations, including the **LetsDefend SOC Analyst Learning Path**.

The purpose of this repository is not to provide walkthrough answers or reproduce training-platform content. Instead, it documents my **investigative methodology, analytical reasoning, technical findings, detection logic, and incident-response recommendations** using sanitized lab evidence.

---

## Portfolio Objectives

This portfolio demonstrates my ability to:

* Triage and investigate security alerts
* Distinguish true positives from false positives
* Analyze phishing emails and malicious infrastructure
* Investigate suspicious authentication activity
* Analyze endpoint, SIEM, network, and web telemetry
* Investigate malware and malicious documents
* Enrich indicators of compromise using threat intelligence
* Reconstruct incident timelines
* Determine incident scope and potential impact
* Map adversary activity to the MITRE ATT&CK framework
* Develop Splunk searches and detection logic
* Document investigations using professional SOC reporting practices
* Recommend containment, remediation, and detection improvements

---

# Investigation Methodology

My investigations generally follow the workflow:

**Alert → Triage → Evidence Collection → Investigation → IOC Enrichment → Timeline Reconstruction → MITRE ATT&CK Mapping → Scope Assessment → Verdict → Containment → Detection Opportunities → Lessons Learned**

I avoid relying on a single indicator or reputation score when determining whether activity is malicious. Findings are based on correlation between available telemetry, observed behavior, threat intelligence, and contextual evidence.

---

# Featured Investigations

This section will contain selected investigations that best demonstrate my SOC analysis capabilities.

| Case    | Investigation | Classification | Verdict | MITRE ATT&CK |
| ------- | ------------- | -------------- | ------- | ------------ |
| SOC-001 | Coming soon   | —              | —       | —            |
| SOC-002 | Coming soon   | —              | —       | —            |
| SOC-003 | Coming soon   | —              | —       | —            |
| SOC-004 | Coming soon   | —              | —       | —            |
| SOC-005 | Coming soon   | —              | —       | —            |

As investigations are completed, each case will link directly to its full report.

---

# Investigation Categories

## Phishing Analysis

Investigations involving:

* Sender analysis
* Email-header analysis
* SPF, DKIM, and DMARC validation
* URL analysis
* Attachment analysis
* Credential-harvesting infrastructure
* Domain and IP reputation
* User-impact assessment

Location:

`investigations/phishing/`

---

## Malware Analysis

Investigations involving:

* Static analysis
* Dynamic analysis
* File hashes
* Process execution
* Child processes
* Registry modifications
* Persistence mechanisms
* Network connections
* Command-and-control indicators

Location:

`investigations/malware/`

---

## Web Attack Analysis

Investigations involving potentially malicious web activity such as:

* SQL injection
* Cross-site scripting
* Directory traversal
* Command injection
* Exploitation attempts
* Suspicious HTTP requests

Location:

`investigations/web-attacks/`

---

## Authentication Investigations

Investigations involving:

* Brute-force attacks
* Password spraying
* Credential attacks
* Abnormal authentication
* Suspicious login activity

Location:

`investigations/authentication/`

---

## Network Investigations

Investigations involving:

* DNS traffic
* HTTP/HTTPS activity
* Firewall telemetry
* Proxy logs
* Suspicious outbound connections
* Command-and-control behavior
* Network indicators of compromise

Location:

`investigations/network/`

---

## SIEM Investigations

Cases focused on:

* Alert triage
* Log correlation
* Search pivots
* Host investigation
* User investigation
* Timeline construction
* Scope determination

Location:

`investigations/siem/`

---

# Detection Engineering

Investigations should not end with determining what happened.

Where appropriate, I attempt to answer:

> How could this behavior be detected reliably in the future?

Detection content may include:

### Splunk

`detection-engineering/splunk/`

### Sigma

`detection-engineering/sigma/`

### YARA

`detection-engineering/yara/`

Each detection should document:

* Detection hypothesis
* Relevant telemetry
* Query or rule
* Expected malicious behavior
* Possible false positives
* Tuning considerations

---

# Threat Intelligence

Threat-intelligence work includes:

* IOC enrichment
* Domain analysis
* IP reputation
* File-hash investigation
* Infrastructure correlation
* Threat-context research

Tools may include:

* VirusTotal
* URLScan
* WHOIS
* AbuseIPDB
* MITRE ATT&CK
* Other OSINT resources where appropriate

Location:

`threat-intelligence/`

---

# SOC Labs

This section documents security infrastructure and labs I build while developing practical blue-team skills.

Planned areas include:

* SOC home lab
* SIEM deployment
* Windows telemetry
* Sysmon
* Endpoint monitoring
* Network telemetry
* Malware-analysis environment

Location:

`labs/`

---

# Knowledge Base

Concise technical notes supporting my practical investigations are stored under:

`knowledge/`

Topics include:

* SOC fundamentals
* Cyber Kill Chain
* MITRE ATT&CK
* Incident response
* SIEM concepts
* Network security
* Malware-analysis concepts

The emphasis of this repository remains practical investigation rather than certification notes.

---

# Tools & Technologies

This list will expand as my portfolio develops.

### Security Operations

* SIEM
* EDR concepts
* Incident response
* Log analysis
* Threat intelligence

### Platforms & Tools

* LetsDefend
* Splunk
* VirusTotal
* MITRE ATT&CK

### Analysis

* Windows Event Logs
* Network logs
* Web logs
* Email headers
* IOC enrichment

### Detection Engineering

* SPL
* Sigma
* YARA

---

# Certifications & Training

### CompTIA Security+

Completed.

### LetsDefend SOC Analyst Learning Path

In progress.

Training areas include:

* SOC fundamentals
* Cyber Kill Chain
* MITRE ATT&CK
* Phishing analysis
* Web attack detection
* SIEM investigations
* Malware analysis
* Malicious-document analysis
* Network log analysis
* Splunk
* Cyber threat intelligence
* VirusTotal
* Brute-force detection
* SOC lab development

---

# Investigation Reporting Standard

Each major investigation is documented using a consistent incident-report format containing:

1. Executive Summary
2. Alert Information
3. Investigation Objective
4. Initial Triage
5. Evidence Collected
6. Investigation Process
7. Indicators of Compromise
8. Timeline
9. MITRE ATT&CK Mapping
10. Scope Assessment
11. Verdict
12. Containment & Remediation
13. Detection Opportunities
14. Lessons Learned
15. Evidence/Screenshots

This structure is intended to demonstrate not only what was discovered, but **how the conclusion was reached**.

---

# Evidence Handling

All investigation material published in this repository is sanitized.

I do not intentionally publish:

* Credentials
* API keys
* Session tokens
* Personally identifiable information
* Sensitive customer information
* Challenge flags
* Direct answers to training-platform assessments
* Confidential organizational data

Screenshots and logs are included only when they contribute directly to the investigation narrative.

---

# Disclaimer

The investigations in this repository are conducted in authorized lab, training, simulation, or personally controlled environments.

They are documented for educational and professional portfolio purposes.

No activity documented here is intended to target systems without authorization.

---

# Current Focus

My current objective is to develop the practical competencies required for an entry-level SOC Analyst role by repeatedly performing and documenting investigations involving:

**Detection → Investigation → Analysis → Response → Detection Improvement**

This repository will continue to evolve as my technical skills and investigation experience develop.
