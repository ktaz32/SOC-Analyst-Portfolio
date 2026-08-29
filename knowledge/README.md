# SOC Knowledge Base

This directory contains operational reference material that supports the investigations in this portfolio.

The goal is not to reproduce course notes. Each reference is written around the questions a SOC analyst needs to answer during an investigation:

- What telemetry matters?
- What behavior is normal?
- What makes an event suspicious?
- What evidence would confirm the activity?
- What cannot be concluded from the available data?
- How should the behavior be mapped to MITRE ATT&CK?
- What detection opportunities follow from the investigation?

---

# Current Knowledge References

| Topic | Location | Practical Focus |
|---|---|---|
| Cyber Kill Chain | [`cyber-kill-chain/`](./cyber-kill-chain/) | Investigation pivots across attack stages |
| MITRE ATT&CK | [`MITRE-ATT&CK/`](./MITRE-ATT&CK/) | Evidence-based tactics/techniques/sub-techniques mapping |
| Phishing Email Analysis | [`Phishing-email-analysis/`](./Phishing-email-analysis/) | Headers, sender validation, URLs, attachments, delivery impact |
| Detecting Web Attacks | [`detecting-web-attacks/`](./detecting-web-attacks/) | HTTP, SQLi, XSS, IDOR, LFI, response analysis |
| Detecting Web Attacks 2 | [`detecting-web-attacks-2/`](./detecting-web-attacks-2/) | Brute force, traversal, open redirect, XXE, defensive patterns |
| SIEM Alert Investigation | [`siem-alert-investigation/`](./siem-alert-investigation/) | Triage, evidence pivots, scoping, verdict, closure |
| Malware Analysis Fundamentals | [`malware-analysis-fundamentals/`](./malware-analysis-fundamentals/) | Static/dynamic analysis, sandboxing, processes, persistence, network behavior |
| Dynamic Malware Analysis | [`dynamic-malware-analysis/`](./dynamic-malware-analysis/) | Process Hacker, Procmon, Regshot, Wireshark, Fiddler, persistence, timelines |

---

# Core Analyst Principles

## Evidence Before Conclusion

A detection rule, IOC reputation result, or automated sandbox verdict is the beginning of analysis.

Where possible, correlate:

```text
Alert
 + SIEM logs
 + Endpoint telemetry
 + Network activity
 + Sandbox behavior
 + Threat intelligence
 + User / host context
```

## Evidence vs Inference

### Direct Evidence
What the logs or artifacts explicitly show.

### Analyst Inference
What can reasonably be concluded.

### Not Established
What cannot be proven.

This distinction prevents unsupported claims about:

- exploitation success
- malware execution
- C2
- persistence
- credential compromise
- lateral movement
- exfiltration

## Detection Is Not Compromise

```text
SQLi payload observed
≠ database compromise confirmed
```

```text
malicious attachment delivered
≠ malware execution confirmed
```

```text
outbound connection observed
≠ C2 automatically confirmed
```

```text
SMTP session observed
≠ data exfiltration automatically confirmed
```

---

# Investigation-Oriented Workflow

```text
Understand technology
        ↓
Identify expected behavior
        ↓
Identify anomaly
        ↓
Collect relevant telemetry
        ↓
Normalize / decode
        ↓
Correlate sources
        ↓
Assess success and impact
        ↓
Map supported ATT&CK behavior
        ↓
Document verdict + confidence
        ↓
Identify detection improvements
```

---

# Malware Analysis Reference Areas

The knowledge base now includes both malware-analysis fundamentals and a dedicated dynamic-analysis guide.

Current coverage includes:

- file hashes and reputation
- static vs dynamic analysis
- malicious Office documents
- VBA/macros
- sandbox analysis
- process trees
- short-lived child processes
- Procmon filtering
- file-system activity
- `%TEMP%`, `%APPDATA%`, Startup locations
- Run / RunOnce persistence
- scheduled tasks
- WMI
- Process Hacker
- Regshot
- Wireshark
- Fiddler
- DNS / HTTP / SMTP analysis
- dropped payloads
- ransomware recovery inhibition
- anti-analysis / delayed execution
- IOC extraction
- behavioral detection opportunities

---

# Detection Engineering Mindset

The knowledge material is also used to derive detection hypotheses.

Examples:

```text
Office process
+
unexpected child process
+
outbound network connection
```

```text
unknown executable
+
AppData file creation
+
Run-key modification
+
outbound SMTP
```

```text
rare executable
+
shadow-copy deletion
+
mass file modification
```

Strong detections should consider:

- expected baselines
- false positives
- process ancestry
- time windows
- multiple telemetry sources
- negative test cases
- tuning boundaries

---

# Current Topics

- SOC fundamentals
- Cyber Kill Chain
- MITRE ATT&CK
- phishing / email
- HTTP fundamentals
- web-server logs
- SQL injection
- XSS
- IDOR
- LFI / RFI
- brute force
- malware-analysis fundamentals
- dynamic malware analysis
- process / file / registry / network behavior
- persistence
- IOC enrichment
- SIEM investigation
- incident response
- detection engineering

---

# Future Expansion

Planned areas include:

- Windows Event IDs
- Sysmon
- PowerShell logging
- Active Directory
- authentication attacks
- DNS / firewall analysis
- threat hunting
- Splunk SPL
- Sigma
- YARA
- memory forensics
- disk forensics

---

# Purpose

The knowledge base supports the portfolio workflow:

**Understand → Detect → Investigate → Validate → Scope → Respond → Improve**

The emphasis remains on practical analyst reasoning and evidence interpretation.
