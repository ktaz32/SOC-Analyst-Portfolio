# SOC Analyst Portfolio

I’m Khaled Taseen, a Computer Science student at Simon Fraser University focused on Security Operations, Blue Team security, incident response, DFIR, and detection engineering.

I have completed the **LetsDefend SOC Analyst Learning Pathway** and built a hands-on SOC portfolio documenting investigations across phishing, malware, web attacks, threat intelligence, endpoint activity, network forensics, and false-positive analysis.

My work includes alert triage, SIEM/log analysis, endpoint investigation, IOC enrichment, malware analysis, MITRE ATT&CK mapping, incident classification, containment decisions, detection tuning, Splunk, Windows Event Log analysis, threat intelligence, and defensive security automation.

---

## Current Milestone

- Completed **LetsDefend SOC Analyst Learning Pathway**
- Completed **CompTIA Security+**
- Built a growing portfolio of documented SOC investigations
- Hands-on work across phishing, malware, web attacks, DFIR, threat intelligence, Splunk, and detection engineering
- Continuing toward stronger junior SOC / MDR analyst readiness
- Preparing for **BTL1**

---

## Featured Investigations

These are selected investigations that best represent my analyst reasoning and evidence-handling approach.

### SOC-004 — Malicious Office Attachment / CVE-2017-11882
Investigation of a malicious password-protected Office attachment that exploited CVE-2017-11882, executed through `EQNEDT32.EXE`, and retrieved a secondary payload.

**Skills:** phishing analysis, malware triage, sandboxing, proxy correlation, endpoint containment, ATT&CK mapping

### SOC-011 — Successful Command Injection
Investigation of a successful command-injection attack against a web server, including commands such as `whoami`, `uname`, and attempts to access `/etc/passwd` and `/etc/shadow`.

**Skills:** web-attack investigation, log correlation, endpoint validation, attack scoping, escalation

### SOC-013 — Emotet Malware Detected
Malware investigation involving Emotet detection, endpoint containment, historical host-context review, and strict separation between direct case evidence and unrelated historical telemetry.

**Skills:** malware triage, evidence validation, containment, IOC analysis, C2 validation methodology

### SOC-017 — Ransomware Detected
Critical ransomware investigation involving a malicious executable, third-party sandbox enrichment, endpoint review, artifact collection, and containment.

**Skills:** ransomware triage, malware analysis, containment, IOC extraction, behavioral analysis

### SOC-018 — Threat Intelligence URL Alert — TapScanner Redirect
Threat-intelligence alert investigation that demonstrated false-positive reasoning, URL-shortener analysis, redirect validation, and cautious use of reputation data.

**Skills:** CTI enrichment, proxy analysis, false-positive validation, redirect-chain reasoning

### SOC-019 — Malicious Macro Document Download Attempt Blocked
Investigation of a malicious macro-enabled Office document with VirusTotal enrichment and careful distinction between sample capability, blocked execution, and confirmed endpoint behavior.

**Skills:** malicious-document analysis, hash validation, endpoint review, ATT&CK validation, event-time correlation

---

## Featured Projects

### Detection-as-Code Pipeline
A security engineering project focused on creating, validating, and managing detections as code.

Key areas:
- Sigma rules
- detection validation
- version control
- CI workflows
- repeatable detection engineering

### AWS Cloud Security Assessment
Hands-on AWS security assessment work covering cloud configuration review and security controls.

Key areas:
- IAM
- cloud security posture
- access control
- security review
- risk identification

### NIST / GRC Gap Assessment Project
A practical governance, risk, and compliance project covering control assessment and risk documentation.

Key areas:
- NIST CSF
- gap assessment
- risk register
- maturity assessment
- control evaluation
- evidence-based findings

---

## Investigation Methodology

My investigations follow a repeatable SOC workflow:

```text
Alert
→ Triage
→ Evidence Collection
→ Log / Telemetry Analysis
→ IOC Enrichment
→ Timeline Construction
→ MITRE ATT&CK Validation
→ Scope Assessment
→ Verdict + Confidence
→ Containment / Response
→ Detection Opportunities
→ Lessons Learned
```

I intentionally separate:
- direct evidence from historical/contextual evidence
- alert-provided ATT&CK mappings from analyst-confirmed mappings
- sandbox capability from endpoint-confirmed behavior
- reputation data from actual compromise evidence

---

## Investigation Categories

My current portfolio includes cases across:
- Phishing and malicious email
- Malicious attachments
- Suspicious URLs
- Malware
- Ransomware
- Web attacks
- Command injection
- SQL injection
- XSS
- LFI / directory traversal
- IDOR
- Threat intelligence
- Network DFIR
- PCAP analysis
- False positives
- Endpoint containment

See the full case index in `Investigations/README.md`.

---

## Detection Engineering

My detection-engineering work focuses on turning investigation findings into reusable detections.

Current and planned areas include:
- Sigma
- Splunk SPL
- Windows Event Logs
- suspicious process chains
- authentication abuse
- malware behavior
- web attack telemetry
- false-positive tuning
- detection-as-code workflows

A strong detection should document:

```text
Detection hypothesis
→ Required telemetry
→ Detection logic
→ False positives
→ Tuning considerations
→ Validation
```

---

## Threat Intelligence

Threat-intelligence work in this portfolio includes:
- IOC enrichment
- VirusTotal
- URL reputation analysis
- redirect-chain validation
- malicious infrastructure review
- C2 candidate extraction
- CTI confidence assessment
- false-positive analysis

I do not treat reputation alone as a verdict.

A stronger workflow is:

```text
IOC
→ Enrichment
→ Freshness check
→ Internal telemetry correlation
→ Context
→ Analyst verdict
```

---

## DFIR and Network Analysis

Current practical work includes:
- Wireshark
- PCAP analysis
- HTTP
- SMTP
- proxy logs
- firewall logs
- endpoint telemetry
- process trees
- registry activity
- persistence analysis
- malware network behavior

---

## Malware Analysis

Current malware-analysis experience includes:
- static analysis
- dynamic analysis
- VirusTotal
- ANY.RUN
- Process Hacker
- Process Monitor
- Wireshark
- Fiddler
- Regshot
- malicious VBA / macro analysis
- dropped-file analysis
- process-tree review
- persistence analysis
- C2 validation

---

## SIEM and Log Analysis

Current SIEM/log-analysis experience includes:
- Splunk
- Windows Event Logs
- Event ID 4624
- Event ID 4625
- authentication correlation
- proxy logs
- firewall logs
- endpoint telemetry
- search/filter workflows
- timeline analysis

I am continuing to build stronger fluency in:
- Splunk SPL
- Microsoft Sentinel
- KQL
- Sysmon
- Windows telemetry

---

## Knowledge Base

The `knowledge/` directory contains practical analyst references built from training and investigation work.

Current topics include:
- Cyber Kill Chain
- MITRE ATT&CK
- Phishing Email Analysis
- Detecting Web Attacks
- Detecting Web Attacks 2
- Malware Analysis
- Malicious Document Analysis
- Dynamic Malware Analysis
- Network Log Analysis
- Security Solutions
- Incident Management
- Splunk
- Cyber Threat Intelligence
- VirusTotal for SOC Analysts
- Brute Force Attack Detection
- SIEM alert investigation
- DFIR concepts

These are written as operational references rather than course walkthroughs.

---

## Tools and Technologies

### Security Operations
- Splunk
- LetsDefend
- VirusTotal
- ANY.RUN
- Wireshark
- Process Monitor
- Process Hacker
- Fiddler
- Regshot

### Detection and Threat Analysis
- MITRE ATT&CK
- Sigma
- IOC enrichment
- malware sandboxing
- Windows Event Viewer

### Scripting / Systems
- Python
- Bash
- Linux
- C
- C++

### Cloud / GRC
- AWS
- IAM
- NIST CSF
- risk assessment
- control assessment

---

## Certifications and Training

### Completed
- **CompTIA Security+**
- **LetsDefend SOC Analyst Learning Pathway**

### In Progress / Planned
- **Blue Team Level 1 (BTL1)**
- continued Splunk / SPL development
- Microsoft Sentinel / KQL
- Windows / Sysmon telemetry
- DFIR and malware-analysis labs
- additional detection-engineering projects

---

## Reporting Standard

Each investigation is written to show analyst reasoning rather than just a final answer.

Typical reports include:
- executive summary
- case information
- initial hypothesis
- evidence review
- analyst decision points
- IOC enrichment
- timeline
- MITRE ATT&CK assessment
- scope
- verdict and confidence
- containment / response
- detection opportunities
- lessons learned

---

## Evidence Handling

Portfolio evidence is documented conservatively.

I avoid:
- claiming successful execution without telemetry
- calling C2 “accessed” without event-time evidence
- treating sandbox behavior as endpoint proof
- blindly trusting alert-provided ATT&CK mappings
- using reputation alone as the verdict
- merging historical host activity into a current case without correlation

This evidence discipline is a core part of the portfolio.

---

## Career Focus

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
→ Cloud security
```

---

## Disclaimer

All investigations and labs in this repository were completed in authorized training environments or personal lab environments.

This repository is intended for defensive security education, analyst skill development, and professional portfolio use.
