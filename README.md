# SOC Analyst Portfolio

I’m Khaled Taseen, a Computer Science student at Simon Fraser University focused on **Security Operations, Blue Team security, detection engineering, cloud security, malware analysis, and incident response**.

This repository documents hands-on cybersecurity work across SOC investigations, phishing and email security, web attacks, malware analysis, network/PCAP analysis, DFIR, SIEM/log correlation, endpoint response, threat intelligence, MITRE ATT&CK mapping, and detection improvement.

I have completed **CompTIA Security+** and continue to build practical analyst capability through authorized labs, structured training, and independent security projects.

The goal of this portfolio is not to reproduce training-platform walkthroughs or challenge answers. It is to demonstrate:

- alert triage and investigation methodology
- evidence collection and correlation
- analyst reasoning and confidence assessment
- true-positive vs false-positive decision making
- IOC enrichment and artifact handling
- static and dynamic malware analysis
- network and endpoint analysis
- MITRE ATT&CK mapping
- containment and remediation decisions
- detection engineering and tuning opportunities
- clear technical reporting

---

# Portfolio Snapshot

| Metric | Current Status |
|---|---:|
| SOC Alert Investigations | **17** |
| Phishing / Email Cases | **5** |
| Web Attack Cases | **6** |
| Malware Alert Cases | **6** |
| Dedicated Malware Analysis Cases | **3** |
| Network / PCAP Cases | **1** |
| DFIR Cases | **1** |
| False-Positive SOC Cases | **4** |
| Total Documented Investigation / Analysis Cases | **22** |

> Counts reflect the cases currently included in this repository.

---

# Featured Projects

These standalone repositories complement the investigation work in this portfolio and demonstrate broader defensive-security capability.

| Project | Focus | Highlights |
|---|---|---|
| [Detection-as-Code Pipeline](https://github.com/ktaz32/Detection-as-Code-Pipeline) | Detection Engineering / DevSecOps | Sigma detections, Python validation, positive/negative tests, GitHub Actions CI, ATT&CK mapping, correlation detections, analyst playbooks |
| [AWS Cloud Security Assessment](https://github.com/ktaz32/AWS-Cloud-Security-Assessment) | Cloud Security / AWS | IAM least privilege, S3 access control, resource-policy analysis, EC2 security groups, CloudTrail validation, before/after remediation evidence |
| [NIST CSF 2.0 Gap Assessment](https://github.com/ktaz32/NIST-CSF-2.0-Gap-Assessment) | GRC / Risk Management | NIST CSF 2.0 maturity assessment, evidence-based findings, risk register, likelihood × impact scoring, remediation roadmap, executive reporting |

## Detection-as-Code Pipeline

The **Detection-as-Code Pipeline** treats security detections as testable software.

It includes:

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

The **AWS Cloud Security Assessment** documents hands-on security review and remediation across AWS services.

Current areas include:

- IAM over-permissioning
- least-privilege remediation
- S3 identity-policy scoping
- S3 bucket-policy analysis
- unintended resource-based access
- EC2 security-group exposure
- CloudTrail investigation and validation
- before-and-after evidence
- remediation verification

## NIST CSF 2.0 Gap Assessment

The **NIST CSF 2.0 Gap Assessment** demonstrates governance, risk, and control-assessment skills.

The project includes:

- assessment across Govern, Identify, Protect, Detect, Respond, and Recover
- evidence-based cybersecurity findings
- maturity scoring
- likelihood × impact risk analysis
- formal risk register
- remediation prioritization
- validation criteria
- executive-level reporting
- maturity and risk visualizations

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
| [MAL-003](./Investigations/malware-analysis/MAL-003-law-exe-dynamic-malware-analysis/MAL-003-law-exe-dynamic-malware-analysis/) | Dynamic Analysis of `law.exe` | Malware Analysis | — | **Malicious** | Procmon, Process Hacker, Wireshark, SMTP, persistence analysis |
| [PCAP-001](./Investigations/network/PCAP-001-http-basic-auth-analysis/) | HTTP Basic Authentication Exposure | Network / PCAP | — | **Security Finding** | Wireshark, stream reconstruction, credential exposure |
| [DFIR-001](./Investigations/DFIR/DFIR-001-multi-stage-web-attack-investigation/) | Multi-Stage Web Attack Investigation | DFIR | High | **Successful Compromise** | Attack-chain reconstruction, brute force, code injection, persistence |

> See the complete [Investigation Index](./Investigations/README.md).

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

I avoid relying on a single alert label, reputation score, or sandbox verdict.

Where possible, findings are correlated across:

- SIEM telemetry
- email-security data
- proxy and firewall logs
- web-server logs
- endpoint/EDR evidence
- process trees
- browser and terminal history
- packet captures
- malware sandbox behavior
- threat intelligence
- user and host context

---

# Analyst Decision Standard

Each report separates:

## Direct Evidence

What the available logs, artifacts, endpoint data, or sandbox results explicitly show.

## Analyst Inference

What can reasonably be concluded from those observations.

## Not Established

What cannot be proven with the available telemetry.

This prevents unsupported claims about:

- successful exploitation
- persistence
- credential compromise
- lateral movement
- command and control
- exfiltration
- incident scope

---

# Investigation Categories

## Phishing & Email Security

Location: [`Investigations/phishing/`](./Investigations/phishing/)

Current cases:

```text
SOC-001 through SOC-005
```

Coverage includes malicious URLs, attachments, credential phishing, sender/header analysis, email-delivery validation, Office-document exploitation, false-positive analysis, and endpoint response.

## Web Attack Analysis

Location: [`Investigations/web-attacks/`](./Investigations/web-attacks/)

Current cases:

```text
SOC-006 through SOC-011
```

Coverage includes LFI/directory traversal, SQL injection, IDOR, XSS, command injection, web-detection false positives, successful compromise validation, and escalation.

## Malware & Ransomware Investigations

Location: [`Investigations/malware-analysis/`](./Investigations/malware-analysis/)

SOC cases:

```text
SOC-012 through SOC-017
```

Dedicated malware-analysis cases:

```text
MAL-001 through MAL-003
```

Coverage includes:

- malicious executables
- Emotet
- macro-enabled Office files
- ransomware
- static malware analysis
- VBA deobfuscation
- dynamic malware analysis
- process trees
- Procmon
- Process Hacker
- Regshot
- Wireshark
- Fiddler
- sandbox analysis
- persistence
- outbound infrastructure correlation
- false-positive validation

## Network / PCAP Analysis

Location: [`Investigations/network/`](./Investigations/network/)

Current case:

```text
PCAP-001
```

## DFIR

Location: [`Investigations/DFIR/`](./Investigations/DFIR/)

Current case:

```text
DFIR-001
```

---

# Detection Engineering

Investigations should not end when a verdict is reached.

Where appropriate, I ask:

> How could this behavior be detected earlier, more reliably, and with fewer false positives?

Investigation-derived detection ideas include:

- malicious-domain access
- risky password-protected attachments
- malicious file hashes
- Office → suspicious child process
- Office → outbound network activity
- SQLi/XSS/command-injection patterns
- IDOR enumeration
- credential-file access
- HTTP Basic Authentication over plaintext
- AppData executable creation
- Run-key persistence
- direct SMTP from unusual processes
- ransomware recovery inhibition
- false-positive tuning for legitimate software installers

The dedicated [Detection-as-Code Pipeline](https://github.com/ktaz32/Detection-as-Code-Pipeline) extends this work into tested, version-controlled detection engineering.

---

# Knowledge Base

Operational references are stored under [`knowledge/`](./knowledge/).

Current topics include:

- Cyber Kill Chain
- MITRE ATT&CK
- Phishing Email Analysis
- Detecting Web Attacks
- Detecting Web Attacks 2
- SIEM Alert Investigation Workflow
- Malware Analysis Fundamentals
- Dynamic Malware Analysis

The knowledge base is written as **practical analyst reference material**, not certification-study notes.

---

# Tools & Technologies

## SOC / Investigation

- SIEM and log analysis
- EDR concepts and containment
- incident response
- threat intelligence
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

Hands-on areas covered include:

- SOC fundamentals
- phishing investigations
- web attack analysis
- SIEM/log investigation
- threat-intelligence enrichment
- endpoint containment
- malware analysis fundamentals
- static malware analysis
- dynamic malware analysis
- sandbox/process-tree analysis
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

I do not intentionally publish:

- credentials
- API keys
- tokens
- challenge flags
- confidential information
- unnecessary personally identifiable information
- raw training answers that do not contribute to analyst reasoning

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
│   │   └── MAL-001 ... MAL-003
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
│   ├── siem-alert-investigation/
│   ├── malware-analysis-fundamentals/
│   └── dynamic-malware-analysis/
├── detection-engineering/
├── security labs/
└── templates/
```

---

# Current Focus

I am continuing to develop deeper capability in:

- SOC investigation and threat hunting
- Windows endpoint analysis
- DFIR
- malware analysis
- detection engineering
- Splunk / SPL
- Sigma / YARA
- cloud security
- incident response
- Python-based security automation

The goal is to build evidence of **repeatable analyst judgment**, not just complete labs.
