# SOC Knowledge Base

This directory contains concise technical reference material that supports my practical SOC investigations.

The purpose of this section is to maintain **operational analyst notes** that can be referenced during investigations rather than reproduce certification study material or training-platform walkthroughs.

The notes focus on:

- how security concepts appear in real telemetry
- what evidence an analyst should look for
- how to distinguish suspicious activity from confirmed malicious behavior
- how concepts connect to SIEM, EDR, network, email, and web investigations
- how to document findings without overstating the evidence

---

# Current Knowledge References

## Cyber Kill Chain

Location:

`cyber-kill-chain.md`

Covers:

- Reconnaissance
- Weaponization
- Delivery
- Exploitation
- Installation
- Command and Control
- Actions on Objectives

The emphasis is on using the Kill Chain to investigate **backward and forward from an observed event**, rather than simply assigning a stage label.

---

## MITRE ATT&CK

Location:

`mitre-attack/`

Covers:

- ATT&CK matrices
- tactics
- techniques
- sub-techniques
- procedures
- mitigations
- threat groups
- software
- evidence-based ATT&CK mapping

Key analyst principle:

> ATT&CK mappings should describe behavior supported by evidence, not assumptions based on an alert name or malware family.

---

## Phishing Email Analysis

Location:

`phishing-email-analysis/`

Covers:

- sender and infrastructure analysis
- raw email-header interpretation
- Received-chain analysis
- SPF, DKIM, and DMARC
- From / Return-Path / Reply-To comparison
- suspicious URLs
- attachment analysis
- static analysis
- sandbox / dynamic analysis
- cloud-hosting abuse
- phishing IOC enrichment
- delivery and user-impact assessment

Key analyst principles include:

- reputation alone does not determine a verdict
- an SPF pass does not automatically make an email legitimate
- trusted cloud infrastructure can host malicious content
- user interaction should not be assumed without telemetry

---

## Detecting Web Attacks

Location:

`detecting-web-attacks/`

Covers:

- HTTP request and response analysis
- web-server access logs
- URL encoding and decoding
- SQL Injection
- Cross-Site Scripting (XSS)
- Command Injection
- Insecure Direct Object Reference (IDOR)
- Local File Inclusion (LFI)
- Remote File Inclusion (RFI)
- automated scanner detection
- attack-success assessment

The web-attack notes emphasize distinguishing:

```text
Attack Attempt
      ↓
Exploitation Attempt
      ↓
Successful Exploitation
      ↓
Confirmed Impact
```

A malicious request does not automatically prove that exploitation succeeded.

---

# Investigation-Oriented Methodology

These notes are written to support the following analyst workflow:

```text
Alert
  ↓
Understand the technology
  ↓
Identify expected behavior
  ↓
Identify the anomaly
  ↓
Collect relevant telemetry
  ↓
Decode / normalize evidence
  ↓
Correlate across data sources
  ↓
Determine attack technique
  ↓
Assess success and impact
  ↓
Map supported ATT&CK behavior
  ↓
Document findings
```

The goal is to understand **why activity is suspicious**, not simply recognize a keyword.

---

# Core Analyst Principles

## Evidence Before Conclusion

A detection rule or reputation score is the beginning of an investigation, not the final verdict.

Where possible, conclusions should be based on correlation between:

- alert telemetry
- SIEM logs
- endpoint data
- network activity
- email telemetry
- HTTP requests
- sandbox behavior
- threat intelligence
- user and host context

---

## Evidence vs Inference

Investigation notes should distinguish:

### Direct Evidence

What logs or artifacts explicitly show.

### Analyst Inference

What can reasonably be concluded from those observations.

### Not Established

What cannot be proven with the available evidence.

This prevents unsupported claims about:

- exploitation success
- persistence
- credential compromise
- lateral movement
- command and control
- exfiltration

---

## Detection Is Not the Same as Compromise

Examples:

```text
SQL injection payload observed
≠
database compromise confirmed
```

```text
XSS payload observed
≠
JavaScript execution confirmed
```

```text
phishing email received
≠
user clicked the link
```

```text
malicious attachment delivered
≠
malware executed
```

Each stage requires supporting evidence.

---

# HTTP and Web Analysis Reference

For web investigations, important fields include:

| Field | Analyst Value |
|---|---|
| Source IP | Identifies request origin |
| HTTP Method | GET, POST, PUT, etc. |
| URI | Identifies target resource |
| Query Parameters | Common attack location |
| Request Body | Important for POST-based attacks |
| User-Agent | Can reveal browsers or automated tools |
| Cookie | May contain session information |
| Response Code | Helps assess application behavior |
| Response Size | May indicate different application responses |
| Request Frequency | Helps identify automation |
| Timestamp | Supports timeline construction |

Web payloads should be decoded before classification whenever encoding or obfuscation is present.

---

# Common Web Attack Indicators

## SQL Injection

Common indicators:

```text
SELECT
UNION
AND
OR
WHERE
EXTRACTVALUE
CAST
CHR
'
--
%27
```

---

## Cross-Site Scripting

Common indicators:

```text
<script>
alert(
prompt(
document.cookie
console.log(
%3Cscript%3E
```

---

## Command Injection

Common indicators:

```text
whoami
ls
dir
cat
id
uname
;
&&
||
|
```

---

## IDOR

Common patterns:

```text
?id=1
?id=2
?id=3
```

or repeated enumeration such as:

```text
user_id=15
user_id=16
user_id=17
```

---

## Local File Inclusion

Common indicators:

```text
../
../../
../../../etc/passwd
/etc/shadow
```

---

## Remote File Inclusion

Common indicators:

```text
?page=http://external-host/file
?page=https://external-host/payload
```

---

# Email Analysis Reference

Important fields include:

- From
- To
- Subject
- Return-Path
- Reply-To
- Message-ID
- Received
- Authentication-Results
- SPF
- DKIM
- DMARC
- attachment hashes
- embedded URLs

Email legitimacy should be evaluated through **identity alignment and telemetry correlation**, not a single authentication result.

---

# IOC Handling

Not every collected artifact is malicious.

Examples of case context that may be benign include:

- internal IP addresses
- legitimate organizational domains
- internal users
- trusted cloud platforms
- normal mail servers

Indicators should be classified according to evidence.

Useful IOC categories include:

- malicious
- suspicious
- benign
- internal context
- unverified

---

# Detection Engineering Mindset

These notes are also used to identify detection opportunities.

Rather than detecting only exact strings, I try to identify behavioral patterns.

Examples:

### Phishing

```text
external sender
+
brand mismatch
+
suspicious URL
+
user interaction
```

### SQL Injection

```text
SQL syntax
+
encoded special characters
+
same vulnerable parameter
+
high request frequency
```

### IDOR

```text
same endpoint
+
many changing object IDs
+
short time window
```

### Exploit Activity

```text
Office process
+
unexpected child process
+
outbound connection
```

Detection logic should also consider:

- false positives
- environmental baselines
- request rate
- response behavior
- correlation across data sources

---

# Topics Covered

Current knowledge areas include:

- SOC fundamentals
- Cyber Kill Chain
- MITRE ATT&CK
- phishing analysis
- email authentication
- HTTP fundamentals
- web-server logs
- SQL injection
- XSS
- command injection
- IDOR
- LFI / RFI
- malware-analysis concepts
- IOC enrichment
- incident-response methodology
- evidence handling
- detection engineering

---

# Future Knowledge Areas

As the portfolio develops, this section may expand to include:

- Windows Event IDs
- Windows authentication telemetry
- Active Directory
- Sysmon
- PowerShell logging
- endpoint process trees
- DNS analysis
- firewall analysis
- network protocols
- malware behavior
- persistence mechanisms
- privilege escalation
- lateral movement
- Splunk SPL
- Sigma
- YARA
- threat hunting

---

# Repository Structure

```text
knowledge/
│
├── README.md
│
├── cyber-kill-chain.md
│
├── mitre-attack/
│   ├── mitre-attack.md
│   └── assets/
│
├── phishing-email-analysis/
│   ├── phishing-email-analysis.md
│   └── assets/
│
└── detecting-web-attacks/
    ├── README.md
    └── images/
```

---

# Purpose

The knowledge base exists to support the investigation workflow:

**Understand → Detect → Investigate → Validate → Scope → Respond → Improve Detection**

Notes are updated as concepts are encountered during hands-on SOC investigations and training.

The emphasis remains on **practical analyst reasoning and evidence interpretation**, not memorization.
