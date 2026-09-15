# SOC Analyst Portfolio

I’m Khaled Taseen, a Computer Science student at Simon Fraser University focused on **Security Operations, Blue Team security, incident response, DFIR, threat intelligence, malware analysis, and detection engineering**.

I have completed the **LetsDefend SOC Analyst Learning Pathway** and **CompTIA Security+**, and I’m building a practical portfolio around evidence-based SOC investigations rather than course walkthroughs.

My work includes:

- alert triage and investigation
- SIEM / log analysis
- endpoint investigation
- IOC enrichment and threat intelligence
- phishing and malicious-document analysis
- malware and ransomware analysis
- web attack investigation
- network / PCAP analysis
- MITRE ATT&CK validation
- incident classification and containment
- false-positive analysis and detection tuning
- Splunk and Windows Event Log analysis
- detection engineering and automation

---

## Quick Navigation

- [Investigation Index](./Investigations/README.md)
- [Knowledge Base](./knowledge/README.md)
- [Detection Engineering](./detection-engineering/README.md)
- [Security Labs](./security-labs/README.md)
- [Templates](./templates/)

---

## Current Milestone

- **Completed:** LetsDefend SOC Analyst Learning Pathway
- **Completed:** CompTIA Security+
- **19 SOC alert investigations**
- **3 dedicated malware-analysis cases**
- **1 Network / PCAP case**
- **1 DFIR case**
- **24 total documented investigation / analysis cases**
- **5 false-positive SOC investigations**
- **17 operational knowledge-base references**
- Preparing for **BTL1**
- Continuing deeper work in Splunk, Windows telemetry, DFIR, malware analysis, threat intelligence, and detection engineering

---

# Featured Investigations

These are selected cases that best demonstrate investigation depth, evidence handling, and analyst judgment.

### [SOC-004 — Malicious Office Attachment / CVE-2017-11882](./Investigations/phishing/SOC-004-malicious-office-attachment-cve-2017-11882/)

Investigation of a malicious password-protected Office attachment exploiting CVE-2017-11882, with process and proxy correlation leading to a secondary payload.

**Skills:** phishing analysis, malicious document triage, exploit analysis, sandboxing, network correlation, containment

---

### [SOC-008 — Successful IDOR Attack](./Investigations/web-attacks/SOC-008-successful-idor-attack/)

Investigation of sequential object access against a vulnerable web endpoint with repeated `200` responses and changing response sizes consistent with unauthorized object retrieval.

**Skills:** HTTP analysis, IDOR recognition, response comparison, attack-success validation, containment

---

### [SOC-011 — Successful Command Injection / Host Compromise](./Investigations/web-attacks/SOC-011-successful-command-injection/)

Investigation of successful command injection against a Linux web server, including `whoami`, `uname`, `/etc/passwd`, and `/etc/shadow` access attempts.

**Skills:** web attack analysis, endpoint validation, Linux telemetry, post-exploitation analysis, escalation

---

### [SOC-017 — Ransomware Detected on MarkPRD](./Investigations/malware-analysis/SOC-017-ransomware-detected-true-positive-v2/)

Critical ransomware investigation supported by sandbox behavior, endpoint evidence, artifact review, recovery-inhibition activity, and containment.

**Skills:** ransomware triage, ANY.RUN, malware behavior, ATT&CK validation, recovery inhibition, incident containment

---

### [SOC-018 — Threat Intelligence URL Alert / TapScanner Redirect](./Investigations/threat-intelligence/soc-018-threat-intel-url-tapscanner-false-positive/)

Threat-intelligence alert investigation that demonstrated false-positive reasoning, URL-shortener analysis, redirect validation, and cautious interpretation of reputation data.

**Skills:** CTI enrichment, proxy analysis, redirect-chain reasoning, scan-freshness awareness, false-positive validation

---

### [SOC-019 — Malicious Macro Document Download Attempt](./Investigations/malware-analysis/soc-019-malicious-docm-download-attempt-blocked/)

Investigation of a malicious macro-enabled Word document with strong VirusTotal consensus, blocked execution, hash-type validation, and event-time C2 qualification.

**Skills:** malicious-document analysis, VirusTotal, hash validation, endpoint review, ATT&CK qualification, evidence vs inference

---

### [MAL-003 — Dynamic Analysis of `law.exe`](./Investigations/malware-analysis/MAL-003-law-exe-dynamic-malware-analysis/MAL-003-law-exe-dynamic-malware-analysis/)

Dedicated malware-analysis case using Process Hacker, Procmon, Wireshark, SMTP analysis, and persistence review.

**Skills:** dynamic malware analysis, process trees, registry persistence, network analysis, SMTP

---

### [PCAP-001 — HTTP Basic Authentication Exposure](./Investigations/network/PCAP-001-http-basic-auth-analysis/)

PCAP investigation demonstrating plaintext HTTP Basic Authentication exposure through Wireshark and TCP stream reconstruction.

**Skills:** Wireshark, PCAP analysis, protocol reconstruction, credential exposure analysis

---

### [DFIR-001 — Multi-Stage Web Attack Investigation](./Investigations/DFIR/DFIR-001-multi-stage-web-attack-investigation/)

DFIR investigation reconstructing reconnaissance, directory brute force, authentication brute force, code injection, command execution, and local-account persistence.

**Skills:** attack-chain reconstruction, web logs, brute force, code injection, persistence, timeline analysis

---

> View all cases in the [complete Investigation Index](./Investigations/README.md).

---

# Featured Projects

These standalone repositories complement the SOC investigation portfolio and demonstrate broader security engineering, cloud security, and GRC capability.

### [Detection-as-Code Pipeline](https://github.com/ktaz32/Detection-as-Code-Pipeline)

A detection-engineering project focused on treating security detections as testable, version-controlled software.

**Key areas:**

- Sigma rules
- Python validation
- positive / negative behavioral tests
- GitHub Actions CI
- MITRE ATT&CK mapping
- correlation detections
- false-positive tuning
- analyst playbooks

```text
Threat behavior
      ↓
Telemetry
      ↓
Detection logic
      ↓
Positive + negative tests
      ↓
Automated validation
      ↓
CI pass / fail
```

---

### [AWS Cloud Security Assessment](https://github.com/ktaz32/AWS-Cloud-Security-Assessment)

Hands-on AWS security assessment work covering cloud configuration review and remediation.

**Key areas:**

- IAM least privilege
- S3 access control
- resource-policy review
- EC2 security groups
- CloudTrail visibility
- remediation validation
- before / after evidence

---

### [NIST CSF 2.0 Gap Assessment](https://github.com/ktaz32/NIST-CSF-2.0-Gap-Assessment)

A practical GRC project focused on evidence-based control assessment and risk management.

**Key areas:**

- NIST CSF 2.0
- Govern / Identify / Protect / Detect / Respond / Recover
- maturity assessment
- gap analysis
- risk register
- likelihood × impact scoring
- remediation roadmap
- executive reporting

---

# Investigation Methodology

My investigations generally follow this workflow:

```text
Alert / Artifact / Packet Capture / Log Set
        ↓
Initial Triage
        ↓
Evidence Collection
        ↓
Log / Endpoint / Network Analysis
        ↓
Threat Intelligence / IOC Enrichment
        ↓
Static / Dynamic / Packet Analysis
        ↓
Timeline Reconstruction
        ↓
Scope Assessment
        ↓
MITRE ATT&CK Validation
        ↓
Verdict + Confidence
        ↓
Containment / Escalation / Remediation
        ↓
Detection Improvement
        ↓
Case Closure
```

I deliberately separate:

- **Direct Evidence**
- **Analyst Inference**
- **Not Established**

This prevents unsupported claims about:

- successful exploitation
- malware execution
- persistence
- credential compromise
- lateral movement
- command and control
- exfiltration
- incident scope

---

# Investigation Categories

## [Phishing & Email Security](./Investigations/phishing/)

Current cases:

```text
SOC-001 through SOC-005
```

Coverage includes:

- malicious URLs
- malicious attachments
- email headers
- sender validation
- credential phishing
- Office-document exploitation
- false-positive analysis
- mail-flow validation
- containment

---

## [Web Attack Analysis](./Investigations/web-attacks/)

Current cases:

```text
SOC-006 through SOC-011
```

Coverage includes:

- LFI / directory traversal
- SQL injection
- IDOR
- XSS
- command injection
- false-positive web detections
- exploit-success validation
- Linux endpoint correlation

---

## [Malware & Ransomware Investigations](./Investigations/malware-analysis/)

SOC cases:

```text
SOC-012 through SOC-017
SOC-019
```

Dedicated malware-analysis cases:

```text
MAL-001 through MAL-003
```

Coverage includes:

- malicious executables
- Emotet
- malicious XLSM / DOCM
- ransomware
- static malware analysis
- dynamic malware analysis
- VBA deobfuscation
- process trees
- registry persistence
- VirusTotal
- ANY.RUN
- Procmon
- Process Hacker
- Wireshark
- Fiddler
- false-positive validation

---

## [Threat Intelligence Investigations](./Investigations/threat-intelligence/)

Current case:

```text
SOC-018
```

Coverage includes:

- URL reputation
- shortened URLs
- redirect chains
- shared infrastructure
- VirusTotal scan freshness
- false-positive validation
- ATT&CK qualification

---

## [Network / PCAP Analysis](./Investigations/network/)

Current case:

```text
PCAP-001
```

---

## [DFIR](./Investigations/DFIR/)

Current case:

```text
DFIR-001
```

---

# Detection Engineering

Portfolio detection-engineering notes are stored in:

### [Detection Engineering](./detection-engineering/README.md)

My detection work focuses on turning investigation findings into reusable security logic.

Current areas include:

- Sigma
- Splunk SPL
- Windows Event Logs
- authentication abuse
- suspicious process chains
- malware behavior
- ransomware recovery inhibition
- web attack telemetry
- correlation logic
- false-positive tuning
- detection-as-code workflows

A strong detection should document:

```text
Detection hypothesis
→ Required telemetry
→ Detection logic
→ Positive test
→ Negative test
→ False positives
→ Tuning
→ ATT&CK
→ Analyst response
```

---

# Knowledge Base

The full knowledge index is available here:

### [SOC Knowledge Base](./knowledge/README.md)

Current operational references:

| Topic | Link |
|---|---|
| Cyber Kill Chain | [Open](./knowledge/cyber-kill-chain/) |
| MITRE ATT&CK | [Open](./knowledge/MITRE-ATT&CK/) |
| Phishing Email Analysis | [Open](./knowledge/Phishing-email-analysis/) |
| Detecting Web Attacks | [Open](./knowledge/detecting-web-attacks/) |
| Detecting Web Attacks 2 | [Open](./knowledge/detecting-web-attacks-2/) |
| SIEM 101 | [Open](./knowledge/siem-101/) |
| SIEM Alert Investigation | [Open](./knowledge/siem-alert-investigation/) |
| Incident Management 101 | [Open](./knowledge/incident-management-101/) |
| Network Log Analysis | [Open](./knowledge/network-log-analysis/) |
| Security Solutions | [Open](./knowledge/security-solutions/) |
| Malware Analysis Fundamentals | [Open](./knowledge/malware-analysis-fundamentals/) |
| Dynamic Malware Analysis | [Open](./knowledge/dynamic-malware-analysis/) |
| Malicious Document Analysis | [Open](./knowledge/malicious-document-analysis/) |
| Splunk | [Open](./knowledge/splunk/) |
| Cyber Threat Intelligence | [Open](./knowledge/cyber-threat-intelligence/) |
| VirusTotal for SOC Analysts | [Open](./knowledge/virustotal-soc-analyst/) |
| Detecting Brute Force Attacks | [Open](./knowledge/brute-force-attack-detection/) |

**Current total: 17 operational references.**

---

# SIEM & Log Analysis

Current hands-on coverage includes:

- Splunk
- Windows Event Viewer
- Event ID 4624
- Event ID 4625
- authentication correlation
- proxy logs
- firewall logs
- WAF logs
- NetFlow concepts
- endpoint telemetry
- time-range investigation
- field discovery
- `stats`
- reports
- dashboards
- SIEM ingestion / parsing concepts

I am continuing to deepen:

- Splunk SPL
- Sysmon
- Windows telemetry
- Microsoft Sentinel
- KQL

---

# Threat Intelligence

Current practical CTI work includes:

- IOC enrichment
- VirusTotal
- URL reputation analysis
- redirect-chain analysis
- IOC freshness
- candidate C2 extraction
- attack-surface concepts
- CTI lifecycle
- technical / tactical / operational / strategic intelligence
- SIEM / EDR / Firewall / SOAR integration

My operating principle is:

```text
Reputation
≠ Verdict
```

Instead:

```text
IOC
→ Enrichment
→ Freshness
→ Internal telemetry
→ Context
→ Analyst verdict
```

---

# Malware & Malicious Document Analysis

Current practical experience includes:

- static analysis
- dynamic analysis
- malicious Office documents
- VBA / macro analysis
- deobfuscation
- VirusTotal Detection / Details / Relations / Behavior
- ANY.RUN
- Process Hacker
- Process Monitor
- Regshot
- Wireshark
- Fiddler
- dropped payloads
- persistence analysis
- ransomware behavior
- C2 qualification

---

# DFIR & Network Analysis

Current practical work includes:

- Wireshark
- PCAP analysis
- HTTP
- SMTP
- proxy logs
- firewall logs
- web-server logs
- attack-chain reconstruction
- authentication brute force
- code injection
- persistence
- process trees
- registry activity
- event timelines

---

# Tools & Technologies

## Security Operations

- Splunk
- Windows Event Viewer
- LetsDefend
- Wireshark
- VirusTotal
- ANY.RUN
- Process Monitor
- Process Hacker
- Fiddler
- Regshot

## Detection / Threat Analysis

- MITRE ATT&CK
- Sigma
- IOC enrichment
- malware sandboxing
- Windows authentication events
- threat intelligence

## Programming / Systems

- Python
- Bash
- Linux
- Git / GitHub
- C
- C++

## Cloud / GRC

- AWS IAM
- Amazon S3
- EC2 Security Groups
- CloudTrail
- NIST CSF 2.0
- risk assessment
- control assessment
- risk registers

---

# Certifications & Training

## Completed

- **CompTIA Security+**
- **LetsDefend SOC Analyst Learning Pathway**

## In Progress / Planned

- **Blue Team Level 1 (BTL1)**
- deeper Splunk / SPL work
- Microsoft Sentinel / KQL
- Windows / Sysmon telemetry
- DFIR and malware analysis
- detection engineering projects

---

# Reporting Standard

Major investigation reports generally include:

1. Executive Summary
2. Case Information
3. Investigation Objective
4. Initial Hypothesis
5. Evidence Review
6. Threat Intelligence / Malware Analysis
7. Timeline
8. Indicators / Artifacts
9. MITRE ATT&CK Validation
10. Scope Assessment
11. Evidence vs Inference
12. Analyst Decision Points
13. Final Verdict + Confidence
14. Containment / Remediation
15. Detection Opportunities
16. Lessons Learned
17. Skills Demonstrated
18. Evidence Index

---

# Evidence Handling

I document evidence conservatively.

I avoid:

- claiming successful execution without telemetry
- calling C2 “accessed” without event-time evidence
- treating sandbox behavior as endpoint proof
- blindly copying alert-provided ATT&CK mappings
- using reputation alone as the verdict
- merging historical host activity into current case evidence without correlation

All investigations are completed in authorized training, simulation, or personally controlled environments.

---

# Repository Structure

```text
SOC-Analyst-Portfolio/
├── README.md
├── Investigations/
│   ├── README.md
│   ├── phishing/
│   ├── web-attacks/
│   ├── malware-analysis/
│   ├── threat-intelligence/
│   ├── network/
│   └── DFIR/
├── knowledge/
│   └── README.md
├── detection-engineering/
│   └── README.md
├── security-labs/
│   └── README.md
└── templates/
```

---

# Career Focus

I am targeting entry-level roles such as:

- SOC Analyst
- Junior Security Analyst
- MDR Analyst
- Security Operations Analyst
- Blue Team Analyst

My current priorities are:

```text
SIEM query fluency
→ Windows / Sysmon telemetry
→ Detection engineering
→ DFIR
→ Malware analysis
→ Threat intelligence
→ Cloud security
```

---

# Disclaimer

All investigations and labs in this repository were completed in authorized training environments or personally controlled lab environments.

This repository is intended for defensive security education, analyst skill development, and professional portfolio use.
