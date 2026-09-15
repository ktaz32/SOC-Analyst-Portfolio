# SOC Investigations

This directory contains documented security investigations completed in authorized lab, simulated SOC, network-analysis, malware-analysis, threat-intelligence, and DFIR environments.

The reports are designed to demonstrate alert triage, evidence collection, SIEM/log/endpoint analysis, CTI enrichment, IOC handling, malware analysis, PCAP analysis, timeline reconstruction, ATT&CK validation, scoping, verdicting, response, and detection tuning.

The emphasis is on **how the conclusion was reached**, not on reproducing challenge answers.

---

# Current Case Count

| Category | Cases |
|---|---:|
| SOC Alert Investigations | **19** |
| Dedicated Malware Analysis | **3** |
| Network / PCAP | **1** |
| DFIR | **1** |
| Total Investigation / Analysis Cases | **24** |

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
| [SOC-018](./threat-intelligence/soc-018-threat-intel-url-tapscanner-false-positive/) | Threat-Intelligence URL Alert / TapScanner Redirect | Threat Intelligence | High | False Positive | Redirect-chain analysis, reputation validation, shared-infrastructure reasoning |
| [SOC-019](./malware-analysis/soc-019-malicious-docm-download-attempt-blocked/) | Malicious Macro Document Download Attempt | Malware | Medium | TP — Blocked | Malicious document analysis, hash validation, event-time correlation, C2 qualification |
| [MAL-001](./malware-analysis/MAL-001-remote-working-xlsm-analysis/MAL-001-remote-working-xlsm-analysis/) | Remote Working XLSM Malware Analysis | Malware Analysis | — | Malicious | VirusTotal relations, dropped files, secondary payload analysis |
| [MAL-002](./malware-analysis/MAL-002-malicious-vba-macro-analysis/MAL-002-malicious-vba-macro-analysis/) | Malicious VBA Macro Analysis | Malware Analysis | — | Malicious | VBA deobfuscation, hex decoding, downloader reconstruction, WMI analysis |
| [MAL-003](./malware-analysis/MAL-003-law-exe-dynamic-malware-analysis/MAL-003-law-exe-dynamic-malware-analysis/) | Dynamic Analysis of `law.exe` | Malware Analysis | — | Malicious | Process Hacker, Procmon, Wireshark, SMTP, Run-key persistence |
| [PCAP-001](./network/PCAP-001-http-basic-auth-analysis/) | HTTP Basic Authentication Exposure | Network / PCAP | — | Security Finding | Wireshark, stream reconstruction, fingerprinting, credential exposure |
| [DFIR-001](./DFIR/DFIR-001-multi-stage-web-attack-investigation/) | Multi-Stage Web Attack Investigation | DFIR / Web Logs | High | Successful Compromise | Attack-chain reconstruction, brute force, injection, persistence |

---

# Current Coverage

## Phishing — SOC-001 to SOC-005

Covers malicious URLs, malicious attachments, internal-email false positives, CVE-2017-11882 exploitation, credential phishing, header analysis, mail-flow validation, sandbox analysis, and containment.

## Web Attacks — SOC-006 to SOC-011

Covers LFI/directory traversal, SQL injection, IDOR, XSS, command injection, false-positive tuning, exploit-success validation, Linux endpoint correlation, and escalation.

## Malware & Ransomware — SOC-012 to SOC-017 and SOC-019

Covers malicious executables, Emotet, legitimate-download false positives, malicious XLSM/DOCM documents, ransomware, hash analysis, sandbox behavior, endpoint containment, telemetry limitations, event-time correlation, recovery inhibition, and C2 qualification.

## Threat Intelligence — SOC-018

Covers shortened-URL resolution, redirect-chain validation, shared-infrastructure reasoning, scan-freshness limitations, ATT&CK qualification, and false-positive classification.

## Dedicated Malware Analysis — MAL-001 to MAL-003

Covers VirusTotal relationships, dropped files, VBA deobfuscation, downloader reconstruction, WMI, Process Hacker, Procmon, AppData payloads, Run-key persistence, Wireshark, and SMTP analysis.

## Network / PCAP — PCAP-001

Covers HTTP filtering, TCP stream reconstruction, fingerprinting, Basic Authentication, and credential exposure over plaintext HTTP.

## DFIR — DFIR-001

Covers reconnaissance, directory brute force, authentication brute force, successful-login validation, code injection, command execution, local-account persistence, and attack-chain reconstruction.

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

Not every case follows the same path. PCAP cases emphasize stream reconstruction; DFIR emphasizes chronology; malware cases emphasize file/process/registry/network behavior; threat-intelligence cases emphasize indicator quality and context; false positives emphasize validation and tuning.

---

# Analyst Principles

- An alert, reputation score, or sandbox label starts an investigation; it does not finish it.
- Reports distinguish **Direct Evidence**, **Analyst Inference**, and **Not Established**.
- Reputation is supporting evidence, not a verdict.
- Alert-provided ATT&CK tags are not automatically analyst-confirmed techniques.
- Missing telemetry means **not confirmed**, not **did not happen**.
- Shared infrastructure should not be labeled malicious without destination-level evidence.
- Historical host activity must be separated from event-time evidence.
- `Blocked`, `Cleaned`, and `Allowed` describe control actions; they do not by themselves establish full execution state.

---

# False-Positive Coverage

Current false-positive cases include:

- SOC-003 — routine internal email
- SOC-010 — substring-based `ls` web detection
- SOC-014 — legitimate WinRAR download
- SOC-016 — legitimate WinRAR installer behavior
- SOC-018 — legitimate TapScanner redirect behind a threat-intelligence URL alert

These cases demonstrate contextual analysis, reputation skepticism, and detection-tuning awareness.

---

# Evidence Handling

All cases are completed in authorized training, lab, simulation, or personally controlled environments. Before publishing, I sanitize passwords, credentials, API keys, tokens, challenge flags, unnecessary personal information, and sensitive internal data.

---

# Current Investigation Skills

- phishing and email analysis
- SIEM / log analysis
- web attack analysis
- endpoint triage
- malware triage
- static and dynamic malware analysis
- malicious-document analysis
- process-tree and registry-persistence analysis
- network / PCAP analysis
- threat intelligence / IOC correlation
- ransomware investigation
- Windows authentication analysis
- DFIR timeline reconstruction
- false-positive analysis
- containment reasoning
- detection tuning
