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
