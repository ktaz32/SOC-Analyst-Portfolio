# SOC Analyst Portfolio

I’m Khaled Taseen, a Computer Science student at Simon Fraser University focused on **Security Operations, Blue Team security, detection engineering, cloud security, malware analysis, DFIR, threat intelligence, and incident response**.

This repository documents hands-on cybersecurity work across SOC alert investigations, phishing and email security, web attacks, malware and ransomware, threat-intelligence triage, network/PCAP analysis, DFIR, SIEM/log correlation, Windows authentication analysis, endpoint response, MITRE ATT&CK validation, and detection improvement.

I have completed **CompTIA Security+** and continue to build practical analyst capability through authorized labs, structured training, and independent security projects.

The goal of this portfolio is not to reproduce training-platform walkthroughs or challenge answers. It is to demonstrate:

- alert triage and investigation methodology
- evidence collection and multi-source correlation
- analyst reasoning and confidence assessment
- true-positive vs false-positive decision making
- IOC enrichment and artifact handling
- static and dynamic malware analysis
- network, endpoint, and Windows-event analysis
- threat-intelligence validation
- MITRE ATT&CK mapping based on evidence
- containment and remediation decisions
- detection engineering and tuning opportunities
- clear technical reporting

---

# Portfolio Snapshot

| Metric | Current Status |
|---|---:|
| SOC Alert Investigations | **19** |
| Phishing / Email Cases | **5** |
| Web Attack Cases | **6** |
| Malware / Ransomware SOC Cases | **7** |
| Threat-Intelligence SOC Cases | **1** |
| Dedicated Malware Analysis Cases | **3** |
| Network / PCAP Cases | **1** |
| DFIR Cases | **1** |
| False-Positive SOC Cases | **5** |
| Knowledge-Base References | **17** |
| Total Documented Investigation / Analysis Cases | **24** |

> Counts reflect the cases currently present in this repository.

---

# Featured Projects

These standalone repositories complement the investigation work in this portfolio and demonstrate broader defensive-security capability.

| Project | Focus | Highlights |
|---|---|---|
| [Detection-as-Code Pipeline](https://github.com/ktaz32/Detection-as-Code-Pipeline) | Detection Engineering / DevSecOps | Sigma detections, Python validation, positive/negative tests, GitHub Actions CI, ATT&CK mapping, correlation detections, analyst playbooks |
| [AWS Cloud Security Assessment](https://github.com/ktaz32/AWS-Cloud-Security-Assessment) | Cloud Security / AWS | IAM least privilege, S3 access control, resource-policy analysis, EC2 security groups, CloudTrail validation, before/after remediation evidence |
| [NIST CSF 2.0 Gap Assessment](https://github.com/ktaz32/NIST-CSF-2.0-Gap-Assessment) | GRC / Risk Management | NIST CSF 2.0 maturity assessment, evidence-based findings, risk register, likelihood × impact scoring, remediation roadmap, executive reporting |

## Detection-as-Code Pipeline

The **Detection-as-Code Pipeline** treats security detections as testable software and includes:

- Sigma-based Windows detections
- positive and negative behavioral fixtures
- automated Python validation
- GitHub Actions CI
- Windows Security Event and Sysmon telemetry
- single-event and correlation detections
- MITRE ATT&CK mapping
- false-positive and tuning analysis
- analyst investigation playbooks

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
      ↓
ATT&CK + tuning + playbook
```

## AWS Cloud Security Assessment

The **AWS Cloud Security Assessment** documents hands-on security review and remediation across AWS services, including IAM, S3, EC2 Security Groups, CloudTrail, least privilege, resource-policy analysis, and remediation validation.

## NIST CSF 2.0 Gap Assessment

The **NIST CSF 2.0 Gap Assessment** demonstrates governance, risk, and control-assessment skills across Govern, Identify, Protect, Detect, Respond, and Recover, with maturity scoring, a formal risk register, remediation prioritization, and executive reporting.

Together, these projects demonstrate capability across **SOC operations, detection engineering, cloud security, and GRC/risk management**.

---

# Featured Investigations

Selected cases that best demonstrate investigation depth and evidence correlation:

| Case | Investigation | Category | Severity | Verdict | Key Skills |
|---|---|---|---:|---|---|
| [SOC-004](./Investigations/phishing/SOC-004-malicious-office-attachment-cve-2017-11882/) | Malicious Office Attachment / CVE-2017-11882 | Phishing / Malware | High | **True Positive** | Exploit analysis, SIEM correlation, process/network evidence, containment |
| [SOC-008](./Investigations/web-attacks/SOC-008-successful-idor-attack/) | Successful IDOR Attack | Web Attack | Medium | **True Positive — Successful** | HTTP analysis, object enumeration, response comparison, containment |
| [SOC-011](./Investigations/web-attacks/SOC-011-successful-command-injection/) | Successful Command Injection / Host Compromise | Web / Endpoint | High | **True Positive — Successful** | Command execution, Linux telemetry, post-exploitation, escalation |
| [SOC-015](./Investigations/malware-analysis/SOC-015-suspicious-xlsm-malware/) | Suspicious XLSM Malware with Outbound Infrastructure Contact | Malware | Medium | **True Positive** | Malicious document analysis, firewall correlation, IOC validation |
| [SOC-017](./Investigations/malware-analysis/SOC-017-ransomware-detected-true-positive-v2/) | Ransomware Detected on MarkPRD | Ransomware | Critical | **True Positive** | Ransomware triage, sandbox behavior, recovery inhibition, containment |
| [SOC-018](./Investigations/threat-intelligence/soc-018-threat-intel-url-tapscanner-false-positive/) | Threat-Intelligence URL Alert / TapScanner Redirect | Threat Intelligence | High | **False Positive** | Redirect analysis, reputation validation, shared-infrastructure reasoning |
| [SOC-019](./Investigations/malware-analysis/soc-019-malicious-docm-download-attempt-blocked/) | Malicious Macro Document Download Attempt | Malware | Medium | **True Positive — Blocked** | Macro malware triage, hash validation, event-time correlation, C2 qualification |
| [MAL-003](./Investigations/malware-analysis/MAL-003-law-exe-dynamic-malware-analysis/MAL-003-law-exe-dynamic-malware-analysis/) | Dynamic Analysis of `law.exe` | Malware Analysis | — | **Malicious** | Procmon, Process Hacker, Wireshark, SMTP, persistence analysis |
| [PCAP-001](./Investigations/network/PCAP-001-http-basic-auth-analysis/) | HTTP Basic Authentication Exposure | Network / PCAP | — | **Security Finding** | Wireshark, stream reconstruction, credential exposure |
| [DFIR-001](./Investigations/DFIR/DFIR-001-multi-stage-web-attack-investigation/) | Multi-Stage Web Attack Investigation | DFIR | High | **Successful Compromise** | Attack-chain reconstruction, brute force, code injection, persistence |

> See the complete [Investigation Index](./Investigations/README.md).

---

# Investigation Methodology

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
Analyst Decision + Confidence
        ↓
Containment / Escalation / Remediation
        ↓
Detection Improvement
        ↓
Case Closure
```

I avoid relying on a single alert label, reputation score, or sandbox verdict. Where possible, findings are correlated across SIEM telemetry, email-security data, proxy/firewall logs, web-server logs, endpoint/EDR evidence, process trees, browser/terminal history, packet captures, sandbox behavior, threat intelligence, Windows Security events, and user/host context.

---

# Analyst Decision Standard

Each report separates:

## Direct Evidence
What the available logs, artifacts, endpoint data, or sandbox results explicitly show.

## Analyst Inference
What can reasonably be concluded from those observations.

## Not Established
What cannot be proven with the available telemetry.

This prevents unsupported claims about successful exploitation, execution, persistence, credential compromise, lateral movement, command and control, exfiltration, or incident scope.

---

# Investigation Categories

## Phishing & Email Security

Location: [`Investigations/phishing/`](./Investigations/phishing/)

```text
SOC-001 through SOC-005
```

Coverage includes malicious URLs, malicious attachments, email false positives, CVE-2017-11882 exploitation, credential phishing, sender/header validation, mail-flow analysis, and endpoint response.

## Web Attack Analysis

Location: [`Investigations/web-attacks/`](./Investigations/web-attacks/)

```text
SOC-006 through SOC-011
```

Coverage includes LFI/directory traversal, SQL injection, IDOR, XSS, command injection, detection false positives, attack-success validation, and escalation.

## Malware & Ransomware

Location: [`Investigations/malware-analysis/`](./Investigations/malware-analysis/)

```text
SOC-012 through SOC-017
SOC-019
MAL-001 through MAL-003
```

Coverage includes malicious executables, Emotet, macro-enabled Office files, ransomware, malicious-document downloaders, static analysis, VBA deobfuscation, dynamic analysis, process trees, Procmon, Process Hacker, Regshot, Wireshark, Fiddler, sandbox analysis, persistence, outbound-infrastructure correlation, and false-positive validation.

## Threat Intelligence

Location: [`Investigations/threat-intelligence/`](./Investigations/threat-intelligence/)

```text
SOC-018
```

Coverage includes shortened-URL analysis, redirect-chain validation, reputation assessment, shared-infrastructure reasoning, and evidence-based false-positive classification.

## Network / PCAP

Location: [`Investigations/network/`](./Investigations/network/)

```text
PCAP-001
```

## DFIR

Location: [`Investigations/DFIR/`](./Investigations/DFIR/)

```text
DFIR-001
```

---

# Detection Engineering

Investigations should not end when a verdict is reached. Investigation-derived detection ideas now include:

- malicious-domain and malicious-URL access
- risky password-protected attachments
- Office → suspicious child process
- Office → outbound network activity
- macro document → PowerShell / remote download behavior
- SQLi / XSS / command-injection patterns
- IDOR enumeration
- credential-file access
- HTTP Basic Authentication over plaintext
- AppData executable creation
- Run-key persistence
- direct SMTP from unusual processes
- ransomware recovery inhibition
- threat-intelligence indicator confidence / expiration
- URL-shortener redirect resolution
- repeated Windows 4625 failures followed by 4624 success
- false-positive tuning for legitimate software installers

See [`detection-engineering/`](./detection-engineering/) and the standalone [Detection-as-Code Pipeline](https://github.com/ktaz32/Detection-as-Code-Pipeline).

---

# Knowledge Base

Operational references are stored under [`knowledge/`](./knowledge/).

Current knowledge references include:

- Cyber Kill Chain
- MITRE ATT&CK
- Phishing Email Analysis
- Detecting Web Attacks
- Detecting Web Attacks 2
- SIEM 101
- SIEM Alert Investigation
- Incident Management 101
- Network Log Analysis
- Security Solutions
- Malware Analysis Fundamentals
- Dynamic Malware Analysis
- Malicious Document Analysis
- Splunk
- Cyber Threat Intelligence
- VirusTotal for SOC Analysts
- Detecting Brute Force Attacks

The knowledge base is written as **practical analyst reference material**, not certification-study notes.

---

# Tools & Technologies

## SOC / SIEM / Investigation

- Splunk / SPL fundamentals
- SIEM and log analysis
- Windows Event Viewer
- Windows Security Events 4624 / 4625
- EDR concepts and containment
- incident response / incident management
- threat intelligence / CTI
- IOC enrichment
- email-security analysis
- proxy and firewall analysis
- web-log analysis
- timeline reconstruction

## Malware / DFIR

- VirusTotal
- ANY.RUN
- Hybrid Analysis
- Process Hacker
- Process Monitor / Procmon
- Regshot
- Wireshark
- Fiddler
- CyberChef
- static and dynamic malware analysis
- VBA / malicious-document analysis
- process-tree analysis
- registry persistence
- file-system analysis

## Detection Engineering

- Sigma
- Python
- GitHub Actions
- positive / negative behavioral tests
- MITRE ATT&CK
- correlation detections
- analyst playbooks
- Splunk SPL — developing
- YARA — developing

## Cloud / GRC

- AWS IAM
- Amazon S3
- EC2 Security Groups
- CloudTrail
- least privilege
- NIST CSF 2.0
- risk assessment
- risk registers
- remediation validation

## Programming / Systems

- Python
- Bash
- Linux
- Git / GitHub
- C / C++

---

# Certifications & Training

## CompTIA Security+

**Completed**

## LetsDefend SOC Analyst Learning Path

**In Progress**

Hands-on areas now documented include:

- SOC fundamentals
- phishing investigations
- web attack analysis
- SIEM/log investigation
- incident management
- threat-intelligence enrichment
- endpoint containment
- Windows authentication / brute-force analysis
- malware analysis fundamentals
- malicious-document analysis
- static malware analysis
- dynamic malware analysis
- sandbox/process-tree analysis
- VirusTotal analysis
- Splunk fundamentals and Windows log ingestion
- Wireshark / PCAP analysis
- DFIR-style investigation

---

# Reporting Standard

Major investigation reports generally include:

1. Executive Summary
2. Case Information
3. Investigation Objective
4. Initial Triage / Hypothesis
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

# Evidence & Safety

All investigations are conducted in authorized training, simulated SOC, or personally controlled environments.

I do not intentionally publish credentials, API keys, tokens, challenge flags, confidential information, unnecessary personally identifiable information, or raw training answers that do not contribute to analyst reasoning.

Screenshots and logs are retained only when they support a meaningful analytical point.

---

# Repository Structure

```text
SOC-Analyst-Portfolio/
├── README.md
├── Investigations/
│   ├── README.md
│   ├── phishing/
│   │   └── SOC-001 ... SOC-005
│   ├── web-attacks/
│   │   └── SOC-006 ... SOC-011
│   ├── malware-analysis/
│   │   ├── SOC-012 ... SOC-017
│   │   ├── SOC-019
│   │   └── MAL-001 ... MAL-003
│   ├── threat-intelligence/
│   │   └── SOC-018
│   ├── network/
│   │   └── PCAP-001
│   └── DFIR/
│       └── DFIR-001
├── knowledge/
│   ├── cyber-kill-chain/
│   ├── MITRE-ATT&CK/
│   ├── Phishing-email-analysis/
│   ├── detecting-web-attacks/
│   ├── detecting-web-attacks-2/
│   ├── siem-101/
│   ├── siem-alert-investigation/
│   ├── incident-management-101/
│   ├── network-log-analysis/
│   ├── security-solutions/
│   ├── malware-analysis-fundamentals/
│   ├── dynamic-malware-analysis/
│   ├── malicious-document-analysis/
│   ├── splunk/
│   ├── cyber-threat-intelligence/
│   ├── virustotal-soc-analyst/
│   └── brute-force-attack-detection/
├── detection-engineering/
├── security-labs/
└── templates/
```

---

# Current Focus

I am continuing to develop deeper capability in:

- SOC investigation and threat hunting
- Windows endpoint and authentication analysis
- DFIR
- malware and malicious-document analysis
- detection engineering
- Splunk / SPL
- Sigma / YARA
- Active Directory and identity security
- cloud security
- incident response
- Python-based security automation

The goal is to build evidence of **repeatable analyst judgment**, not just complete labs.
