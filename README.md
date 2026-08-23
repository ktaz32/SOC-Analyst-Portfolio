# SOC Analyst Portfolio

Welcome to my cybersecurity portfolio.

This repository documents my practical development as a **Security Operations Center (SOC) Analyst**, with a focus on alert triage, phishing analysis, malicious-file investigation, web-attack analysis, SIEM/log correlation, endpoint containment, network/PCAP analysis, DFIR, threat intelligence, MITRE ATT&CK mapping, and detection improvement.

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
| SOC Alert Investigations | **11** |
| Phishing / Email Cases | **5** |
| Web Attack Cases | **6** |
| Network / PCAP Cases | **1** |
| DFIR Cases | **1** |
| False-Positive Cases | **2** |
| Total Documented Investigation Cases | **13** |

> Counts will continue to grow as new investigations and technical projects are added.

---

# Featured Investigations

These are selected cases that best demonstrate investigation depth, evidence correlation, and defensive reasoning.

| Case | Investigation | Category | Severity | Verdict | MITRE ATT&CK | Key Skills |
|---|---|---|---:|---|---|---|
| [SOC-004](./Investigations/phishing/SOC-004-malicious-office-attachment-cve-2017-11882/) | Malicious Office Attachment / CVE-2017-11882 | Phishing / Malware | High | **True Positive** | T1566.001, T1203, T1105 | Malware analysis, exploit recognition, SIEM correlation, process/network analysis, EDR containment |
| [SOC-008](./Investigations/web-attacks/SOC-008-successful-idor-attack/) | Successful IDOR Attack | Web Attack | Medium | **True Positive — Successful** | T1190 | IDOR analysis, object enumeration, response comparison, containment, escalation |
| [SOC-011](./Investigations/web-attacks/SOC-011-successful-command-injection/) | Successful Command Injection / Host Compromise | Web Attack / Endpoint | High | **True Positive — Successful** | T1190, T1059.004, T1033, T1082, T1003.008 | Command injection, Linux endpoint telemetry, post-exploitation analysis, containment, Tier 2 escalation |
| [PCAP-001](./Investigations/network/PCAP-001-http-basic-auth-analysis/) | HTTP Basic Authentication Exposure | Network / PCAP | — | **Security Finding** | None | Wireshark, HTTP stream reconstruction, fingerprinting, credential-exposure analysis |
| [DFIR-001](./Investigations/DFIR/DFIR-001-multi-stage-web-attack-investigation/) | Multi-Stage Web Attack Investigation | DFIR / Web Logs | High | **Successful Compromise with Persistence Attempt** | T1595.002, T1110.001, T1078, T1059, T1033, T1136.001 | Attack-chain reconstruction, Nikto detection, brute force, code injection, persistence analysis |

> Full investigation coverage is available in the [Investigations index](./Investigations/).

---

# Investigation Highlights

## SOC-004 — Malicious Office Attachment / CVE-2017-11882

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

## SOC-008 — Successful IDOR Attack

An external source repeatedly queried the same object endpoint while changing `user_id` values.

Investigation identified:

- sequential object enumeration
- repeated HTTP `200` responses
- varying response sizes
- external-to-internal attack direction
- successful unauthorized object-access pattern

The target web server was contained and the case required escalation.

**Outcome:** True Positive / Successful IDOR Exploitation

---

## SOC-011 — Successful Command Injection / Host Compromise

An external attacker submitted commands through a vulnerable POST parameter:

```text
ls
whoami
uname
cat /etc/passwd
cat /etc/shadow
```

Endpoint Security terminal history independently confirmed execution of multiple attacker-supplied commands.

The sequence progressed from command-execution validation to:

- user discovery
- system discovery
- local-account enumeration
- attempted access to credential material

The affected Linux web server was contained and the incident was escalated to Tier 2.

**Outcome:** True Positive / Confirmed Host Compromise

---

## PCAP-001 — HTTP Basic Authentication Exposure

A packet capture was analyzed in Wireshark.

Analysis identified:

- 5 HTTP GET requests
- FreeBSD server fingerprint
- Apache/2.2.15
- OpenSSL/0.9.8n
- Lynx client User-Agent
- HTTP Basic Authentication credentials recoverable from plaintext traffic

The credential password was intentionally redacted from the public report.

**Finding:** Plaintext HTTP exposed reusable Basic Authentication credentials.

---

## DFIR-001 — Multi-Stage Web Attack Investigation

Raw web access logs were analyzed to reconstruct an entire attack chain:

```text
Nikto reconnaissance
        ↓
Directory brute force
        ↓
Login brute force
        ↓
Successful authentication
        ↓
Code injection
        ↓
System command execution
        ↓
Persistence attempt
```

**Outcome:** Successful Multi-Stage Web Compromise with Persistence Attempt

---

# Investigation Methodology

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
Static / Dynamic / Packet Analysis
        ↓
Timeline Reconstruction
        ↓
Scope Assessment
        ↓
MITRE ATT&CK Mapping
        ↓
Analyst Decision
        ↓
Containment / Escalation / Remediation
        ↓
Detection Improvement
        ↓
Case Closure
```

I avoid relying on a single indicator, reputation score, or alert label.

Findings are based on correlation between:

- SIEM telemetry
- email-security data
- proxy/network logs
- firewall and web-server logs
- endpoint evidence
- browser and terminal history
- packet captures
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

Techniques observed across current cases include:

- **T1566.001 — Spearphishing Attachment**
- **T1566.002 — Spearphishing Link**
- **T1204.001 — User Execution: Malicious Link**
- **T1203 — Exploitation for Client Execution**
- **T1105 — Ingress Tool Transfer**
- **T1190 — Exploit Public-Facing Application**
- **T1059.004 — Command and Scripting Interpreter: Unix Shell**
- **T1033 — System Owner/User Discovery**
- **T1082 — System Information Discovery**
- **T1003.008 — OS Credential Dumping: `/etc/passwd` and `/etc/shadow`**
- **T1595.002 — Active Scanning: Vulnerability Scanning**
- **T1110.001 — Brute Force: Password Guessing**
- **T1078 — Valid Accounts**
- **T1136.001 — Create Account: Local Account**

If no malicious adversary behavior is established, no ATT&CK technique is assigned.

---

# Investigation Categories

## Phishing & Email Security

Current work includes phishing URLs, malicious attachments, credential-phishing links, internal-email false positives, Office-document exploitation, email-delivery validation, SMTP/source analysis, URL analysis, and sandbox analysis.

Location:

`Investigations/phishing/`

Current cases:

```text
SOC-001 through SOC-005
```

---

## Web Attack Analysis

Current investigations include:

- Local File Inclusion / directory traversal
- SQL injection
- IDOR
- Cross-Site Scripting
- command injection
- web-detection false positives
- successful host compromise
- Tier 2 escalation decisions

Location:

`Investigations/web-attacks/`

Current cases:

```text
SOC-006 through SOC-011
```

---

## Network / PCAP Analysis

Current network-analysis work includes:

- Wireshark display filters
- HTTP stream reconstruction
- server fingerprinting
- client fingerprinting
- HTTP header analysis
- Basic Authentication analysis
- credential-exposure assessment

Location:

`Investigations/network/`

Current cases:

```text
PCAP-001
```

---

## DFIR

Current DFIR work includes:

- raw web access-log analysis
- attack-chain reconstruction
- automated scanner identification
- directory brute-force detection
- authentication brute-force analysis
- successful-login validation
- code-injection analysis
- persistence identification

Location:

`Investigations/dfir/`

Current cases:

```text
DFIR-001
```

---

## Malware Analysis

Current experience includes archive analysis, file hashes, malicious Office documents, sandbox analysis, exploit identification, process behavior, and post-execution network activity.

Future malware-specific cases will be stored under:

`Investigations/malware/`

---

## SIEM & Endpoint Analysis

Completed investigations have included proxy telemetry, Exchange logs, firewall logs, source/destination correlation, process-linked network events, browser history, terminal history, endpoint containment, timeline reconstruction, and validation of blocked vs allowed activity.

Future dedicated cases will be stored under:

```text
Investigations/siem/
Investigations/endpoint/
```

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
- contextual internal-email phishing detection
- directory-brute-force detection using request volume and `404` ratios
- SQL injection pattern detection
- XSS payload recognition
- IDOR object-enumeration behavior
- command-injection detection using parameter and shell context
- web-service processes reading `/etc/passwd` or `/etc/shadow`
- Basic Authentication observed over plaintext HTTP
- rule tuning to avoid substring false positives such as `ls` inside `skills`

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
- Web Attack Detection

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
- Wireshark
- VirusTotal
- ANY.RUN
- Hybrid Analysis
- Cisco Talos
- AbuseIPDB
- MITRE ATT&CK
- CyberChef

## Analysis Areas

- Exchange / email telemetry
- Proxy logs
- Firewall logs
- Web access logs
- HTTP traffic
- PCAP analysis
- File hashes
- Office-document analysis
- Linux command activity
- Endpoint process activity
- Browser history
- Terminal history
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
- Web Attack Detection
- SQL Injection analysis
- XSS analysis
- IDOR analysis
- LFI / directory traversal
- Command Injection
- Threat-intelligence enrichment
- Sandbox analysis
- Endpoint containment
- SIEM/log correlation
- Wireshark / PCAP analysis
- DFIR-style web-log investigation

Future learning areas include:

- advanced SIEM investigation
- malware analysis
- network log analysis
- Splunk
- cyber threat intelligence
- authentication attack investigations
- brute-force / password-spraying detection
- Windows endpoint investigation
- Active Directory
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
│   │
│   ├── phishing/
│   │   ├── SOC-001-phishing-url-detected/
│   │   ├── SOC-002-phishing-malicious-attachment/
│   │   ├── SOC-003-internal-email-false-positive/
│   │   ├── SOC-004-malicious-office-attachment-cve-2017-11882/
│   │   └── SOC-005-paypal-phishing-link-challenge/
│   │
│   ├── web-attacks/
│   │   ├── SOC-006-lfi-directory-traversal/
│   │   ├── SOC-007-sql-injection-attempt/
│   │   ├── SOC-008-successful-idor-attack/
│   │   ├── SOC-009-xss-attempt/
│   │   ├── SOC-010-false-positive-ls-command-detection/
│   │   └── SOC-011-successful-command-injection/
│   │
│   ├── network/
│   │   └── PCAP-001-http-basic-auth-analysis/
│   │
│   └── dfir/
│       └── DFIR-001-multi-stage-web-attack-investigation/
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
│   ├── phishing-email-analysis/
│   └── web-attack-detection/
│
└── templates/
    └── investigation-template.md
```

---

# Current Focus

My current objective is to continue building practical SOC capability by repeatedly applying the full investigation cycle:

**Detection → Triage → Investigation → Analysis → Scope → Response → Detection Improvement**

The next stages of this portfolio will expand further into:

- malware analysis
- Windows endpoint investigations
- Active Directory
- authentication attacks
- SIEM correlation
- Splunk
- detection engineering
- threat hunting
- incident response
- Linux security
- Python security tooling
- Bash automation
- DFIR
- SOC lab development

This repository will continue to evolve as my hands-on investigation experience develops.
