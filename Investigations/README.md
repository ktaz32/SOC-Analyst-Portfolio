# SOC Investigations

This directory contains documented security investigations completed in authorized lab and simulated SOC environments.

Each case is written as a professional SOC investigation report and is designed to demonstrate:

- Alert triage
- Evidence collection
- Log and telemetry analysis
- Threat-intelligence enrichment
- IOC handling
- Timeline reconstruction
- MITRE ATT&CK mapping
- Scope assessment
- Analyst decision-making
- Final verdict and confidence
- Containment and remediation recommendations
- Detection opportunities
- Lessons learned

The goal of these reports is to show **how conclusions were reached**, rather than reproduce training-platform walkthroughs or challenge answers.

---

## Investigation Index

| Case | Investigation | Category | Severity | Verdict | MITRE ATT&CK | Key Skills |
|---|---|---|---|---|---|---|
| [SOC-001](./phishing/SOC-001-phishing-url-detected/) | Phishing URL Detected | Phishing / Proxy | High | True Positive | T1204.001 | Proxy analysis, IOC enrichment, access validation, EDR containment |
| [SOC-002](./phishing/SOC-002-phishing-malicious-attachment/) | Malicious Phishing Attachment Blocked | Phishing / Email | Medium | True Positive | T1566.001 | Email analysis, attachment analysis, sandboxing, mail-flow validation |
| [SOC-003](./phishing/SOC-003-internal-email-false-positive/) | Internal Email Phishing Alert | Phishing / Email | Medium | False Positive | None | False-positive analysis, email-content review, sender validation, detection-tuning awareness |
| [SOC-004](./phishing/SOC-004-malicious-office-attachment-cve-2017-11882/) | Malicious Office Attachment / CVE-2017-11882 | Phishing / Malware | High | True Positive | T1566.001, T1203, T1105 | Malware analysis, exploit recognition, SIEM correlation, process/network analysis, EDR containment |


---

## Current Investigation Categories

### Phishing

Current phishing cases include:

- **SOC-001 — Phishing URL Detected**
  - Confirmed access to a malicious phishing domain
  - Proxy request was allowed
  - Affected endpoint identified and contained
  - Final verdict: True Positive

- **SOC-002 — Malicious Phishing Attachment Blocked**
  - Malicious password-protected attachment identified
  - Threat-intelligence and sandbox analysis confirmed malicious behavior
  - Email was blocked before user delivery
  - Final verdict: True Positive

- **SOC-003 — Internal Email Phishing Alert**
  - Internal-to-internal email triggered a phishing detection rule
  - Message content was consistent with routine business communication
  - No URLs, attachments, credential requests, or suspicious social-engineering indicators were identified
  - No evidence of account compromise or malicious follow-on activity was observed
  - Final verdict: False Positive

- **SOC-004 — Malicious Office Attachment / CVE-2017-11882**
  - Invoice-themed phishing email containing a password-protected malicious attachment was delivered to the recipient
  - Static and sandbox analysis identified malicious Office-document behavior associated with CVE-2017-11882
  - SIEM correlation showed `EQNEDT32.EXE`, parented by `excel.exe`, making an allowed outbound request to malicious infrastructure
  - Malicious email was removed from the recipient mailbox
  - Affected endpoint was contained through EDR
  - Final verdict: True Positive


Additional categories will be added as investigations are completed.

Planned areas include:

- Malware
- Web attacks
- Authentication attacks
- Network investigations
- SIEM investigations
- Endpoint investigations

---

## Investigation Methodology

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
Scope Assessment
  ↓
MITRE ATT&CK Mapping
  ↓
Analyst Decision
  ↓
Containment / Response
  ↓
Detection Improvement
  ↓
Case Closure
