# SOC Investigations

This directory contains documented security investigations completed in authorized lab, simulated SOC, network-analysis, malware-analysis, and DFIR environments.

The reports are designed to demonstrate:

- alert triage
- evidence collection
- SIEM / log / endpoint analysis
- threat-intelligence enrichment
- IOC and artifact handling
- static and dynamic malware analysis
- network and PCAP analysis
- timeline reconstruction
- MITRE ATT&CK validation
- scope assessment
- analyst decision-making
- verdict and confidence
- containment / remediation
- detection opportunities
- false-positive tuning

The emphasis is on **how the conclusion was reached**, not on reproducing challenge answers.

---

# Investigation Index

| Case | Investigation | Category | Severity | Verdict | Key Skills |
|---|---|---|---|---|---|
| [SOC-001](./phishing/SOC-001-phishing-url-detected/) | Phishing URL Detected | Phishing / Proxy | High | True Positive | Proxy analysis, IOC enrichment, access validation, containment |
| [SOC-002](./phishing/SOC-002-phishing-malicious-attachment/) | Malicious Phishing Attachment Blocked | Phishing / Email | Medium | True Positive | Email analysis, attachment analysis, sandboxing, mail-flow validation |
| [SOC-003](./phishing/SOC-003-internal-email-false-positive/) | Internal Email Phishing Alert | Phishing / Email | Medium | False Positive | False-positive analysis, sender/context validation, tuning |
| [SOC-004](./phishing/SOC-004-malicious-office-attachment-cve-2017-11882/) | Malicious Office Attachment / CVE-2017-11882 | Phishing / Malware | High | True Positive | Exploit recognition, SIEM correlation, process/network analysis, containment |
| [SOC-005](./phishing/SOC-005-paypal-phishing-link-challenge/) | PayPal-Themed Credential Phishing | Phishing / Email | High | True Positive | Header analysis, URL analysis, infrastructure validation, IOC enrichment |
| [SOC-006](./web-attacks/SOC-006-lfi-directory-traversal-attempt/) | LFI / Directory Traversal Attempt | Web Attack | High | TP — Unsuccessful | HTTP analysis, LFI recognition, response interpretation |
| [SOC-007](./web-attacks/SOC-007-sql-injection-attempt/) | Multiple SQL Injection Attempts | Web Attack | High | TP — Unsuccessful | SQLi analysis, URL decoding, multi-event correlation |
| [SOC-008](./web-attacks/SOC-008-successful-idor-attack/) | Successful IDOR Attack | Web Attack | Medium | TP — Successful | Object enumeration, HTTP response comparison, containment |
| [SOC-009](./web-attacks/SOC-009-xss-attempt/) | Cross-Site Scripting Attempt | Web Attack | Medium | TP — Execution Not Established | XSS analysis, response interpretation, evidence qualification |
| [SOC-010](./web-attacks/SOC-010-false-positive-ls-command-detection/) | False Positive `ls` Detection | Web / Tuning | High | False Positive | Browser-history correlation, contextual validation, tuning |
| [SOC-011](./web-attacks/SOC-011-successful-command-injection/) | Successful Command Injection / Host Compromise | Web / Endpoint | High | TP — Successful | Linux telemetry, command execution, post-exploitation, escalation |
| [SOC-012](./malware-analysis/SOC-012-malware-detected-outbound-connection/) | Malware with Confirmed Outbound Activity | Malware | — | True Positive | File reputation, proxy correlation, telemetry-gap analysis, containment |
| [SOC-013](./malware-analysis/SOC-013-emotet-malware-detected/) | Emotet Malware Detected | Malware | Medium | True Positive | Malware triage, cleaned-vs-executed reasoning, historical-context separation |
| [SOC-014](./malware-analysis/SOC-014-proxy-malicious-executable-false-positive/SOC-014-proxy-malicious-executable-false-positive/) | Proxy Malicious Executable Alert | Malware / Proxy | Medium | False Positive | Legitimate-download validation, URL reputation, rule tuning |
| [SOC-015](./malware-analysis/SOC-015-suspicious-xlsm-malware/) | Suspicious XLSM Malware with Outbound Contact | Malware | Medium | True Positive | Malicious Office analysis, firewall correlation, IOC validation, containment |
| [SOC-016](./malware-analysis/SOC-016-winrar-installer-false-positive/SOC-016-winrar-installer-false-positive/) | WinRAR Installer Malware Alert | Malware | Medium | False Positive | VirusTotal interpretation, sandbox validation, installer behavior, tuning |
| [SOC-017](./malware-analysis/SOC-017-ransomware-detected-true-positive-v2/) | Ransomware Detected on MarkPRD | Ransomware | Critical | True Positive | Ransomware behavior, recovery inhibition, sandbox analysis, containment |
| [MAL-001](./malware-analysis/MAL-001-remote-working-xlsm-analysis/MAL-001-remote-working-xlsm-analysis/) | Remote Working XLSM Malware Analysis | Malware Analysis | — | Malicious | VirusTotal relations, dropped files, secondary payload analysis |
| [MAL-002](./malware-analysis/MAL-002-malicious-vba-macro-analysis/MAL-002-malicious-vba-macro-analysis/) | Malicious VBA Macro Analysis | Malware Analysis | — | Malicious | VBA deobfuscation, hex decoding, downloader reconstruction, WMI analysis |
| [MAL-003](./malware-analysis/MAL-003-law-exe-dynamic-malware-analysis/MAL-003-law-exe-dynamic-malware-analysis/) | Dynamic Analysis of `law.exe` | Malware Analysis | — | Malicious | Process Hacker, Procmon, Wireshark, SMTP, Run-key persistence |
| [PCAP-001](./network/PCAP-001-http-basic-auth-analysis/) | HTTP Basic Authentication Exposure | Network / PCAP | — | Security Finding | Wireshark, stream reconstruction, fingerprinting, credential exposure |
| [DFIR-001](./DFIR/DFIR-001-multi-stage-web-attack-investigation/) | Multi-Stage Web Attack Investigation | DFIR / Web Logs | High | Successful Compromise | Attack-chain reconstruction, brute force, injection, persistence |

---

# Current Coverage

## Phishing — SOC-001 to SOC-005

The phishing cases cover:

- malicious URL access
- malicious attachments
- internal-email false positives
- CVE-2017-11882 exploitation
- credential-phishing infrastructure
- email headers and sender validation
- mail-flow validation
- sandbox analysis
- endpoint containment

## Web Attacks — SOC-006 to SOC-011

The web cases cover:

- LFI / directory traversal
- SQL injection
- IDOR
- XSS
- command injection
- false-positive detection tuning
- attack-success validation
- Linux endpoint correlation
- Tier 2 escalation

## Malware & Ransomware — SOC-012 to SOC-017

The malware alert cases now cover:

- malicious executable with outbound traffic
- Emotet
- legitimate-download false positive
- malicious XLSM with correlated infrastructure contact
- WinRAR installer false positive
- critical ransomware execution
- threat-intelligence enrichment
- sandbox analysis
- endpoint containment
- telemetry limitations
- recovery inhibition
- false-positive validation

## Dedicated Malware Analysis — MAL-001 to MAL-003

These cases go beyond alert triage and focus on the artifact itself.

### MAL-001 — XLSM Malware Analysis

- multi-engine reputation
- dropped-file relationships
- secondary executable URL
- artifact hashing
- behavior interpretation

### MAL-002 — Malicious VBA Macro Analysis

- static VBA analysis
- hex-string extraction
- downloader URL recovery
- `MSXML2.ServerXMLHTTP`
- `ADODB.Stream`
- `WScript.Shell`
- WMI `Win32_Process`

### MAL-003 — Dynamic Analysis of `law.exe`

- Process Hacker
- Procmon process tree
- file/registry activity
- AppData payload
- Run-key persistence
- Wireshark
- SMTP over TCP/587
- evidence-qualified exfiltration assessment

## Network / PCAP — PCAP-001

- HTTP filtering
- TCP stream reconstruction
- server/client fingerprinting
- Basic Authentication analysis
- credential exposure over plaintext HTTP

## DFIR — DFIR-001

- reconnaissance
- directory brute force
- authentication brute force
- successful-login validation
- code injection
- command execution
- local-account persistence attempt
- attack-chain reconstruction

---

# Investigation Methodology

```text
Alert / Artifact / Packet Capture / Log Set
        ↓
Initial Triage
        ↓
Evidence Collection
        ↓
Process / File / Registry / Network Analysis
        ↓
Threat Intelligence / IOC Enrichment
        ↓
Timeline Reconstruction
        ↓
Scope Assessment
        ↓
ATT&CK Validation
        ↓
Verdict + Confidence
        ↓
Containment / Response
        ↓
Detection Improvement
        ↓
Closure
```

Not every case follows the exact same path:

- **PCAP cases** emphasize filtering and stream reconstruction.
- **DFIR cases** emphasize chronological attack-chain reconstruction.
- **Malware-analysis cases** emphasize process, file, registry, network, and sandbox behavior.
- **False positives** emphasize contextual validation and tuning.
- **Confirmed compromise** emphasizes containment and scoping.

---

# Reporting Standard

Major cases generally include:

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

# Analyst Principles

## Evidence Before Verdict

An alert, reputation score, or sandbox label starts an investigation; it does not finish it.

## Evidence vs Inference

Reports distinguish:

- **Direct Evidence**
- **Analyst Inference**
- **Not Established**

## Reputation Is Supporting Evidence

VirusTotal, ANY.RUN, Hybrid Analysis, Talos, and AbuseIPDB are used to enrich investigations, not replace telemetry.

## ATT&CK Must Be Evidence-Supported

Alert-provided ATT&CK tags are not automatically retained as analyst-confirmed techniques.

## Missing Telemetry Is a Limitation, Not a Negative Finding

Example:

```text
No network logs available
```

means:

```text
C2 not confirmed
```

not:

```text
C2 did not occur
```

## False Positives Matter

The current portfolio includes false-positive investigations involving:

- routine internal email
- substring-based web detection
- legitimate WinRAR download activity
- legitimate WinRAR installer behavior

These cases demonstrate judgment, contextual analysis, and detection-tuning awareness.

---

# Evidence Handling

All cases are completed in authorized training, lab, simulation, or personally controlled environments.

Before publishing, I sanitize:

- passwords
- credentials
- API keys
- tokens
- challenge flags
- unnecessary personal information
- sensitive internal data

Screenshots are retained only when they support an analytical point.

---

# Current Investigation Skills

- phishing and email analysis
- SIEM / log analysis
- web attack analysis
- endpoint triage
- malware triage
- static malware analysis
- dynamic malware analysis
- process-tree analysis
- registry persistence
- network / PCAP analysis
- SMTP analysis
- threat intelligence
- IOC correlation
- ransomware investigation
- DFIR timeline reconstruction
- false-positive analysis
- containment reasoning
- detection tuning
