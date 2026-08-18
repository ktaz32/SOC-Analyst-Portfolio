# SOC Analyst Portfolio

Welcome to my cybersecurity portfolio.

This repository documents my practical development as a **Security Operations Center (SOC) Analyst**, with a focus on alert triage, phishing analysis, malicious-file investigation, SIEM/log correlation, endpoint containment, threat intelligence, MITRE ATT&CK mapping, and detection improvement.

I have completed **CompTIA Security+** and am currently developing hands-on SOC experience through structured lab environments and the **LetsDefend SOC Analyst Learning Path**.

The purpose of this repository is not to provide training-platform walkthroughs or challenge answers. Instead, it documents my:

- investigative methodology
- analytical reasoning
- evidence handling
- technical findings
- incident-scoping decisions
- containment actions
- MITRE ATT&CK mappings
- detection-engineering observations

using sanitized evidence from authorized lab and simulated SOC environments.

---

# Portfolio Snapshot

| Metric | Current Status |
|---|---:|
| Completed SOC Investigations | **4** |
| True Positives | **3** |
| False Positives | **1** |
| Phishing / Email Investigations | **4** |
| Cases with Threat-Intelligence Analysis | **3** |
| Cases with Malware / Sandbox Analysis | **2** |
| Cases Requiring Endpoint Containment | **2** |
| Cases with MITRE ATT&CK Mapping | **3** |

---

# Featured Investigations

| Case | Investigation | Severity | Verdict | MITRE ATT&CK | Key Skills |
|---|---|---:|---|---|---|
| [SOC-001](./Investigations/phishing/SOC-001-phishing-url-detected/) | Phishing URL Detected | High | **True Positive** | T1204.001 | Proxy analysis, IOC enrichment, access validation, EDR containment |
| [SOC-002](./Investigations/phishing/SOC-002-phishing-malicious-attachment/) | Malicious Phishing Attachment Blocked | Medium | **True Positive** | T1566.001 | Email analysis, threat intelligence, sandboxing, mail-flow validation |
| [SOC-003](./Investigations/phishing/SOC-003-internal-email-false-positive/) | Internal Email Phishing Alert | Medium | **False Positive** | None | False-positive analysis, email review, detection-tuning awareness |
| [SOC-004](./Investigations/phishing/SOC-004-malicious-office-attachment-cve-2017-11882/) | Malicious Office Attachment / CVE-2017-11882 | High | **True Positive** | T1566.001, T1203, T1105 | Malware analysis, exploit recognition, SIEM correlation, EDR containment |

> Each investigation is documented as an analyst case study rather than a step-by-step reproduction of the training platform.

---

# Investigation Highlights

## SOC-001 — Phishing URL Detected

A malicious phishing URL was accessed from an internal endpoint.

Key findings included:

- malicious destination confirmed through reputation analysis
- user and source host identified
- proxy request confirmed as **Allowed**
- actual user access verified
- affected endpoint contained through EDR

**Outcome:** True Positive

---

## SOC-002 — Malicious Phishing Attachment Blocked

A COVID-19-themed phishing email contained a password-protected malicious attachment.

Analysis included:

- email-content review
- sender and SMTP investigation
- attachment/hash reputation analysis
- sandbox analysis
- mail-delivery validation

The email-security control successfully blocked the message before delivery.

**Outcome:** True Positive / Successful Prevention

---

## SOC-003 — Internal Email False Positive

An internal-to-internal email triggered a phishing rule.

Investigation confirmed:

- normal internal sender and recipient
- routine meeting request
- no URL
- no attachment
- no malicious or social-engineering indicators

The case was closed without unnecessary containment or ATT&CK mapping.

**Outcome:** False Positive

---

## SOC-004 — Malicious Office Attachment Exploiting CVE-2017-11882

An invoice-themed phishing email containing a password-protected malicious Office attachment bypassed the email gateway.

Investigation correlated:

- malicious archive reputation
- malicious extracted Office document
- CVE-2017-11882 exploit indicators
- `EQNEDT32.EXE` activity
- parent process `excel.exe`
- outbound request to malicious infrastructure
- allowed post-exploitation network traffic

The malicious message was deleted and the endpoint was contained.

**Outcome:** True Positive / Confirmed Endpoint Execution

---

# Investigation Methodology

My investigations generally follow this workflow:

```text
Alert
  ↓
Initial Triage
  ↓
Evidence Collection
  ↓
Log / Telemetry Analysis
  ↓
Threat Intelligence / IOC Enrichment
  ↓
Static / Dynamic Analysis
  ↓
Scope Assessment
  ↓
MITRE ATT&CK Mapping
  ↓
Analyst Decision
  ↓
Containment / Remediation
  ↓
Detection Improvement
  ↓
Case Closure
```

I avoid relying on a single indicator, reputation score, or alert label.

Findings are based on correlation between:

- SIEM telemetry
- mail-security data
- proxy/network logs
- endpoint evidence
- sandbox behavior
- threat intelligence
- user and host context

---

# Analyst Decision Standard

Each investigation attempts to separate three important categories.

## Direct Evidence

What is directly supported by:

- logs
- alerts
- email telemetry
- endpoint data
- sandbox behavior
- threat-intelligence results

## Analyst Inference

What can reasonably be concluded from the evidence.

## Not Established

What cannot be proven from the available telemetry.

This is intended to prevent overstatement of:

- persistence
- credential compromise
- lateral movement
- command and control
- exfiltration
- incident scope

---

# MITRE ATT&CK Mapping Standard

MITRE ATT&CK is used to describe **observed adversary behavior**, not simply the name or default tag of an alert.

Each ATT&CK mapping should answer:

> What evidence in this investigation supports this technique?

Examples from completed cases include:

- **T1566.001 — Spearphishing Attachment**
- **T1204.001 — User Execution: Malicious Link**
- **T1203 — Exploitation for Client Execution**
- **T1105 — Ingress Tool Transfer**

If no malicious adversary behavior is established, no ATT&CK technique is assigned.

---

# Investigation Categories

## Phishing & Email Security

Current investigations include:

- phishing URLs
- malicious attachments
- internal-to-internal email alerts
- Office-document exploitation
- email-delivery validation
- SMTP/source analysis
- sandbox analysis

Location:

`Investigations/phishing/`

---

## Malware Analysis

Current experience includes:

- archive analysis
- file hashes
- malicious Office documents
- sandbox analysis
- process behavior
- exploit identification
- network activity following execution

Future malware-specific cases will be stored under:

`Investigations/malware/`

---

## SIEM & Log Analysis

Completed investigations have included:

- proxy telemetry
- Exchange logs
- source/destination correlation
- process-linked network events
- timeline reconstruction
- validation of blocked vs allowed activity

Future SIEM-focused investigations will be stored under:

`Investigations/siem/`

---

## Future Investigation Areas

As the portfolio develops, additional categories will include:

- Web attacks
- Authentication attacks
- Network investigations
- Endpoint investigations
- Malware investigations
- Brute-force / password-spraying investigations
- Detection-engineering cases

---

# Detection Engineering

Investigations should not end after determining whether an alert is malicious.

Where appropriate, I also ask:

> How could this behavior be detected earlier or more reliably?

Current detection concepts derived from investigations include:

- malicious-domain access allowed by proxy
- password-protected attachment risk scoring
- known-malicious file-hash detection
- phishing campaign correlation
- Office application → `EQNEDT32.EXE`
- `EQNEDT32.EXE` making outbound network connections
- internal-email phishing detection without blanket allowlisting

Detection content will expand under:

`detection-engineering/`

Planned formats include:

- Splunk SPL
- Sigma
- YARA
- detection hypotheses
- false-positive analysis
- tuning considerations

---

# Threat Intelligence

Threat-intelligence enrichment has been used to analyze:

- domains
- URLs
- SMTP IP addresses
- destination IP addresses
- MD5 hashes
- SHA-1 hashes
- SHA-256 hashes
- malicious document reputation
- malware/exploit classifications

Tools used or encountered include:

- VirusTotal
- ANY.RUN
- Hybrid Analysis
- Talos Intelligence
- AbuseIPDB
- MITRE ATT&CK

Threat intelligence is used as **supporting evidence**, not as a replacement for telemetry.

---

# Evidence Handling

Evidence quality is an important part of this portfolio.

My investigation reports follow several principles:

- preserve observed values exactly
- distinguish MD5, SHA-1, and SHA-256
- do not merge conflicting IP observations
- distinguish internal case artifacts from malicious IOCs
- document evidence discrepancies instead of hiding them
- separate observed facts from analyst inference
- avoid unsupported ATT&CK mappings
- retain screenshots only when they support an analytical point

---

# Knowledge Base

Operational SOC notes are stored under:

`knowledge/`

Current topics include:

- Cyber Kill Chain
- MITRE ATT&CK
- Phishing Email Analysis

These notes are written as practical analyst references rather than certification study dumps.

---

# Tools & Technologies

## Security Operations

- SIEM analysis
- EDR concepts and containment
- Incident response
- Email-security analysis
- Proxy/log analysis
- Threat intelligence
- IOC enrichment
- Malware triage

## Platforms & Tools

- LetsDefend
- VirusTotal
- ANY.RUN
- Hybrid Analysis
- Talos Intelligence
- AbuseIPDB
- MITRE ATT&CK

## Analysis Areas

- Exchange / email telemetry
- Proxy logs
- Network telemetry
- File hashes
- Office-document analysis
- Endpoint process activity
- Sandbox behavior
- IOC correlation

## Detection Engineering

Planned and developing:

- Splunk SPL
- Sigma
- YARA

---

# Certifications & Training

## CompTIA Security+

**Completed**

## LetsDefend SOC Analyst Learning Path

**In Progress**

Completed or currently covered areas include:

- SOC Fundamentals
- Cyber Kill Chain
- MITRE ATT&CK
- Phishing Email Analysis
- Phishing alert investigations
- Threat-intelligence enrichment
- Sandbox analysis
- Endpoint containment
- SIEM/log correlation

Future learning areas include:

- Web attack detection
- SIEM investigation
- Malware analysis
- Network log analysis
- Splunk
- Cyber threat intelligence
- Brute-force detection
- SOC lab development

---

# Investigation Reporting Standard

Each major investigation uses a consistent structure including:

1. Executive Summary
2. Case Information
3. Investigation Objective
4. Initial Triage
5. Evidence Review
6. Threat-Intelligence / Malware Analysis
7. Analyst Decision Points
8. Evidence vs Inference
9. MITRE ATT&CK Mapping
10. Scope Assessment
11. IOC / Artifact Record
12. Final Verdict
13. Response Actions
14. Production SOC Analyst Note
15. Detection Opportunities
16. Lessons Learned

The goal is to demonstrate not only **what happened**, but **how the conclusion was reached**.

---

# Evidence and Safety

All investigations are conducted in:

- authorized training environments
- simulated SOC environments
- personally controlled lab environments

I do not intentionally publish:

- credentials
- API keys
- session tokens
- personally identifiable information
- confidential customer information
- challenge flags
- unauthorized data
- direct copies of protected training answers

Screenshots and logs are included only when they contribute to the investigation narrative.

---

# Repository Structure

```text
SOC-Analyst-Portfolio/
│
├── README.md
│
├── Investigations/
│   ├── README.md
│   └── phishing/
│       ├── SOC-001-phishing-url-detected/
│       ├── SOC-002-phishing-malicious-attachment/
│       ├── SOC-003-internal-email-false-positive/
│       └── SOC-004-malicious-office-attachment-cve-2017-11882/
│
├── detection-engineering/
│   └── README.md
│
├── labs/
│   └── README.md
│
├── knowledge/
│   ├── README.md
│   ├── cyber-kill-chain.md
│   ├── mitre-attack/
│   └── phishing-email-analysis/
│
└── templates/
    └── investigation-template.md
```

---

# Current Focus

My current objective is to continue building practical SOC capability by repeatedly applying the full investigation cycle:

**Detection → Triage → Investigation → Analysis → Scope → Response → Detection Improvement**

The next stages of this portfolio will expand beyond phishing into:

- Web attacks
- SIEM investigations
- Authentication attacks
- Malware analysis
- Network investigations
- Splunk
- Detection engineering
- SOC lab development

This repository will continue to evolve as my hands-on investigation experience develops.
