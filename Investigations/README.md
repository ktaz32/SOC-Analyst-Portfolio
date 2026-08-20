# SOC Investigations

This directory contains documented security investigations completed in authorized lab, simulated SOC, network-analysis, and DFIR environments.

Each case is written as a professional investigation report and is designed to demonstrate:

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
| [SOC-005](./phishing/SOC-005-paypal-phishing-link-challenge/) | PayPal-Themed Credential Phishing | Phishing / Email | High | True Positive | T1566.002 | Email-header analysis, sender-infrastructure validation, URL analysis, phishing-page identification, IOC enrichment |
| [SOC-006](./web-attacks/SOC-006-lfi-directory-traversal/) | LFI / Directory Traversal Attempt | Web Attack | High | True Positive — Unsuccessful | T1190 | HTTP analysis, LFI recognition, source-IP enrichment, response-code interpretation, escalation decision |
| [SOC-007](./web-attacks/SOC-007-sql-injection-attempt/) | Multiple SQL Injection Attempts | Web Attack | High | True Positive — Unsuccessful | T1190 | SQLi recognition, multi-event correlation, URL decoding, response analysis, source-IP enrichment |
| [SOC-008](./web-attacks/SOC-008-successful-idor-attack/) | Successful IDOR Attack | Web Attack | Medium | True Positive — Successful | T1190 | IDOR analysis, object-enumeration detection, HTTP response comparison, compromise validation, containment |
| [SOC-009](./web-attacks/SOC-009-xss-attempt/) | Cross-Site Scripting Attack Attempt | Web Attack | Medium | True Positive — Execution Not Established | T1190 | XSS payload analysis, HTTP correlation, source enrichment, evidence-qualified success assessment |
| [SOC-010](./web-attacks/SOC-010-false-positive-ls-command-detection/) | False Positive `ls` Command Detection | Web Attack / Detection Tuning | High | False Positive | None | False-positive validation, browser-history correlation, contextual analysis, rule tuning |
| [SOC-011](./web-attacks/SOC-011-successful-command-injection/) | Successful Command Injection / Host Compromise | Web Attack / Endpoint | High | True Positive — Successful | T1190, T1059.004, T1033, T1082, T1003.008 | Command-injection analysis, Linux endpoint telemetry, attack progression, containment, Tier 2 escalation |
| [PCAP-001](./network/PCAP-001-http-basic-auth-analysis/) | HTTP Basic Authentication Exposure | Network / PCAP | — | Security Finding | None | Wireshark, HTTP filtering, stream reconstruction, server/client fingerprinting, credential-exposure analysis |
| [DFIR-001](./dfir/DFIR-001-multi-stage-web-attack-investigation/) | Multi-Stage Web Attack Investigation | DFIR / Web Logs | High | Successful Compromise with Persistence Attempt | T1595.002, T1110.001, T1078, T1059, T1033, T1136.001 | Attack-chain reconstruction, Nikto identification, directory brute force, login brute force, code injection, persistence analysis |

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

- **SOC-005 — PayPal-Themed Credential Phishing**
  - PayPal-branded German-language email was analyzed as a phishing attempt
  - Header analysis showed sender, Return-Path, and infrastructure inconsistencies
  - Embedded links resolved to a suspicious Google Cloud Storage-hosted page rather than PayPal infrastructure
  - URL reputation analysis classified the destination as malicious/phishing
  - Final verdict: True Positive

---

### Web Attacks

Current web-attack investigations include:

- **SOC-006 — LFI / Directory Traversal Attempt**
  - External source requested `../../../../etc/passwd`
  - HTTP request was permitted but returned `500` with response size `0`
  - Traffic was malicious but successful file disclosure was not established
  - Final verdict: True Positive — Unsuccessful Attack

- **SOC-007 — Multiple SQL Injection Attempts**
  - Four SQL injection payloads were correlated from the same external source
  - Payloads included boolean and `ORDER BY` patterns
  - All observed attempts returned HTTP `500`
  - No successful exploitation was established
  - Final verdict: True Positive — Unsuccessful Attack

- **SOC-008 — Successful IDOR Attack**
  - External source repeatedly queried the same object endpoint with different `user_id` values
  - Requests returned HTTP `200` with different response sizes
  - Object-enumeration behavior was consistent with IDOR exploitation
  - Target web server was contained and the incident escalated
  - Final verdict: True Positive — Successful Attack

- **SOC-009 — Cross-Site Scripting Attack Attempt**
  - Multiple JavaScript/XSS payloads were observed against a search parameter
  - Payloads included `script`, `svg`, `onerror`, and `prompt/alert` patterns
  - HTTP responses returned redirects with zero-byte response bodies
  - Malicious XSS attempts were confirmed, but browser-side script execution was not established
  - Final verdict: True Positive — Execution Not Established

- **SOC-010 — False Positive `ls` Command Detection**
  - Rule triggered because the letters `ls` appeared inside the benign search term `skills`
  - Network logs and endpoint browser history showed normal LetsDefend blog browsing
  - No shell syntax or command-execution evidence was present
  - Case includes detection-tuning recommendations for token-aware matching
  - Final verdict: False Positive

- **SOC-011 — Successful Command Injection / Host Compromise**
  - External source submitted `ls`, `whoami`, `uname`, `cat /etc/passwd`, and `cat /etc/shadow`
  - Requests returned HTTP `200` with varying response sizes
  - Endpoint terminal history confirmed execution of several attacker-supplied commands
  - Affected Linux web server was contained
  - Incident was escalated to Tier 2
  - Final verdict: True Positive — Successful Command Injection / Host Compromise

---

### Network / PCAP Analysis

Current network-analysis cases include:

- **PCAP-001 — HTTP Basic Authentication Exposure**
  - Wireshark filtering identified 5 HTTP GET requests
  - HTTP stream reconstruction exposed server and client fingerprinting information
  - Server identified as FreeBSD running Apache/2.2.15 and OpenSSL/0.9.8n
  - HTTP Basic Authentication credentials were recoverable because they were Base64 encoded over plaintext HTTP
  - Password was intentionally redacted from the public portfolio
  - Primary finding: insecure credential exposure over unencrypted HTTP

---

### DFIR

Current DFIR cases include:

- **DFIR-001 — Multi-Stage Web Attack Investigation**
  - Nikto-based automated reconnaissance identified
  - Directory brute-force activity followed reconnaissance
  - Repeated login requests showed authentication brute force
  - Successful authentication was validated by a `302` redirect followed by authenticated portal access
  - Code injection followed, beginning with a `whoami` payload
  - Later payload attempted persistence by creating a local user account
  - Final assessment: Successful Multi-Stage Web Compromise with Persistence Attempt

---

## Investigation Methodology

My investigations generally follow this workflow:

```text
Alert / Evidence Source
        ↓
Initial Triage
        ↓
Evidence Collection
        ↓
Log / Telemetry Analysis
        ↓
Threat Intelligence / IOC Enrichment
        ↓
Timeline Reconstruction
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
```

Not every case follows the exact same path. For example:

- **PCAP investigations** may begin with packet filtering and stream reconstruction.
- **DFIR investigations** may begin with raw logs and require attack-chain reconstruction.
- **False-positive cases** emphasize contextual validation and detection tuning.
- **Confirmed compromises** emphasize containment, escalation, and post-exploitation scoping.

---

## Reporting Standard

Each major investigation is documented using a consistent structure where appropriate:

1. Executive Summary
2. Case Information
3. Investigation Objective
4. Initial Triage
5. Evidence Collected
6. Investigation Process
7. Indicators / Artifacts
8. Timeline
9. MITRE ATT&CK Mapping
10. Scope Assessment
11. Evidence vs Inference
12. Analyst Decision Points
13. Final Verdict
14. Containment / Remediation
15. Detection Opportunities
16. Lessons Learned
17. Skills Demonstrated
18. Evidence / Screenshots

The emphasis is on **defensible conclusions supported by evidence**.

---

## Evidence Handling

All cases are completed in authorized training, lab, simulation, or personally controlled environments.

Before publishing, I sanitize or remove:

- Passwords
- Credentials
- API keys
- Tokens
- Challenge flags
- Unnecessary personally identifiable information
- Sensitive internal data
- Training-platform answers that do not contribute to the investigation narrative

Screenshots are included only when they materially support the investigation.

---

## Current Coverage

The investigation portfolio currently includes:

- Phishing
- Malicious attachments
- Email false positives
- Proxy investigations
- Web attacks
- LFI / directory traversal
- SQL injection
- IDOR
- XSS
- Command injection
- Detection false positives
- Endpoint containment
- Network / PCAP analysis
- HTTP protocol analysis
- DFIR web-log reconstruction
- Authentication brute force
- Persistence analysis

Future areas will expand into:

- Malware
- Windows endpoint investigations
- Authentication attacks
- SIEM correlation
- Active Directory
- Cloud security
- Threat hunting
- Detection engineering
- Incident response
- Memory and disk forensics
