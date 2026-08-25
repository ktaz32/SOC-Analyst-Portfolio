# SIEM Alert Investigation Workflow

This reference documents a practical, repeatable workflow for investigating SIEM alerts in a Security Operations Center (SOC).

The purpose of this page is not to reproduce a training-platform walkthrough. Instead, it distills the core analyst methodology used across phishing, malware, network, endpoint, and web-attack investigations.

---

## Investigation Lifecycle

A mature SIEM investigation should move through a consistent sequence:

```text
Alert Detection
  ↓
Initial Triage
  ↓
Ownership / Case Creation
  ↓
Evidence Collection
  ↓
Log / Telemetry Analysis
  ↓
Threat Intelligence Enrichment
  ↓
Endpoint / EDR Analysis
  ↓
Scope & Impact Assessment
  ↓
Containment / Response
  ↓
True Positive / False Positive Decision
  ↓
Analyst Documentation
  ↓
Alert Closure
  ↓
Detection Improvement
```

The exact pivots vary by alert type, but the objective remains the same: determine what happened, whether the activity is malicious, how far it progressed, what systems or users are affected, and what response is justified.

---

# 1. Alert Detection & Initial Triage

SIEM alerts are generated when events match predefined detection logic, rules, or correlation conditions.

The first objective is to understand **why the alert fired** before making assumptions about the event.

Review:

- Severity
- Event time
- Rule name
- Event ID
- Alert type
- Source and destination
- Device action
- Hostname
- Username
- Process name
- Requested URL
- Detection trigger reason
- MITRE ATT&CK mapping, if provided

Ask:

> What specific behavior caused this alert to trigger?

Then determine whether the alert is:

- Likely benign
- Suspicious
- Clearly malicious
- Insufficiently evidenced and requiring further investigation

Do not classify an alert solely from the rule name.

---

# 2. Alert Ownership

When an alert requires investigation, take ownership so responsibility is clear and the case can be tracked.

Ownership should establish:

- Assigned analyst
- Investigation start time
- Case status
- Evidence collected
- Decisions taken
- Escalation or containment actions

This prevents duplicated effort and creates accountability across the SOC workflow.

---

# 3. Case Creation & Playbook Initiation

Once an alert is assigned, create a case and begin the appropriate investigation playbook.

A playbook provides a structured process for handling different alert types such as:

- Phishing
- Malware
- Web attacks
- Authentication attacks
- Suspicious network activity
- Endpoint compromise
- Data exfiltration
- Command-and-control activity

The playbook should guide the investigation without replacing analyst judgment.

> Follow the playbook, but validate every conclusion against the available evidence.

---

# 4. Evidence Collection

Before forming a conclusion, gather the evidence that can directly support or reject the alert hypothesis.

Typical evidence sources include:

- SIEM events
- Firewall logs
- Proxy logs
- DNS logs
- Authentication logs
- Email telemetry
- EDR telemetry
- Process trees
- Browser history
- Terminal / command history
- File hashes
- Network connections
- Threat-intelligence results
- Sandbox results

Record timestamps and preserve the relationship between events.

---

# 5. Email Analysis

For phishing and email-based alerts, collect the core message details first.

Review:

- Sender address
- Recipient address
- SMTP / sending IP
- Subject
- Time sent
- Message body
- Embedded URLs
- Attachments
- Email headers
- Authentication results
- Device or mail-gateway action

Questions to answer:

- Does the sender identity make sense?
- Is the message context suspicious?
- Are there attachments or URLs?
- Was the email delivered, blocked, quarantined, or deleted?
- Was the content opened or executed?
- Did follow-on activity occur?

For suspicious files or URLs, use controlled analysis methods such as static analysis, reputation services, URL analysis, file-hash enrichment, sandboxing, and dynamic analysis.

Do not rely on a single vendor verdict.

---

# 6. Network & Log Analysis

Network and log analysis helps determine whether malicious content was accessed, executed, or communicated externally.

Useful pivots include:

- Source IP
- Destination IP
- Domain
- URL
- Process
- Username
- Hostname
- Port
- Timestamp

Review:

- Outbound connections
- Proxy requests
- Firewall actions
- DNS requests
- C2 indicators
- Download activity
- Repeated connection attempts
- Unexpected ports
- Suspicious process-to-network relationships

When a host is suspected of compromise:

1. Identify the affected host.
2. Pivot to all relevant log sources.
3. Search the time window around the alert.
4. Correlate destinations with threat intelligence.
5. Determine whether the connection was allowed or blocked.

---

# 7. Threat Intelligence & IOC Enrichment

Threat intelligence should support the investigation, not decide it.

Common IOC types include:

- IP addresses
- Domains
- URLs
- File hashes
- Email addresses

Useful enrichment questions:

- Has the IOC been associated with malware, phishing, scanning, or C2 activity?
- Is the IOC part of hosting infrastructure or a residential network?
- Is the reputation current or historical?
- Do multiple sources agree?
- Does telemetry show actual interaction with the IOC?

A clean reputation result does **not** prove benign activity.

A malicious reputation result does **not** prove the alert is a true positive without supporting telemetry.

---

# 8. Endpoint / EDR Analysis

Endpoint analysis is used to determine what occurred on the host after the suspicious event.

## Host Context

Review:

- Hostname
- IP address
- Operating system
- Primary user
- Last login
- Client / server role

## Process Analysis

Look for:

- Suspicious executables
- Unusual parent-child relationships
- Office applications spawning interpreters
- Script engines
- LOLBins
- Unknown binaries
- Recently executed files

Examples of high-value relationships:

```text
winword.exe
  └── powershell.exe
```

```text
excel.exe
  └── cmd.exe
```

```text
browser.exe
  └── suspicious.exe
```

## Network Actions

Check whether suspicious processes made:

- Outbound connections
- DNS queries
- C2 connections
- Downloads
- Connections to rare destinations

## Terminal History

Review for:

- Reconnaissance commands
- Credential access
- File discovery
- Persistence
- Remote execution
- Data collection

## Browser History

Review for:

- Malicious sites
- Suspicious downloads
- Credential-harvesting pages
- Redirect chains
- Recently visited attack infrastructure

---

# 9. Scope & Impact Assessment

Determine whether the activity was isolated or part of a wider incident.

Ask:

- How many hosts are affected?
- How many users interacted with the IOC?
- Was the payload executed?
- Was persistence created?
- Was data accessed or exfiltrated?
- Was lateral movement attempted?
- Were credentials exposed?
- Did the attacker obtain command execution?
- Did the activity remain at the attempted stage?

Clearly distinguish between:

```text
Attempted
vs
Delivered
vs
Accessed
vs
Executed
vs
Compromised
```

These are materially different outcomes.

---

# 10. Containment & Response

Containment should be proportional to the evidence and potential impact.

Possible actions include:

- Isolate endpoint
- Delete malicious email
- Block domain
- Block URL
- Block IP
- Disable account
- Reset credentials
- Revoke sessions
- Remove malicious files
- Stop suspicious processes
- Escalate to Tier 2 / Incident Response

Typical reasons for containment include:

- Preventing data loss
- Preventing unauthorized access
- Preventing lateral movement
- Preventing additional malware execution
- Limiting C2 communication
- Preventing further compromise

---

# 11. True Positive vs False Positive Decision

The final verdict should be based on evidence, not the alert label.

## True Positive

Use when the detection correctly identified malicious or unauthorized activity.

Examples:

- Malicious attachment delivered and executed
- Confirmed phishing-link access
- Successful command injection
- C2 communication from a compromised endpoint
- Malicious process execution

## False Positive

Use when the detection fired on legitimate activity.

Examples:

- Benign query string containing a keyword used by an overly broad rule
- Authorized administrative activity
- Known business application behavior
- Expected scanning from approved infrastructure

A strong verdict explains **why**.

---

# 12. Analyst Notes

The analyst note should summarize the investigation in a way another SOC analyst can quickly understand.

A useful structure:

```text
Alert:
What triggered the detection?

Evidence:
What logs, telemetry, or artifacts were reviewed?

Findings:
What activity actually occurred?

Impact:
Was access, execution, or compromise confirmed?

Response:
What containment or remediation actions were taken?

Verdict:
True Positive or False Positive, with confidence level.
```

Avoid vague statements, unsupported assumptions, copying the alert description, or repeating playbook prompts without analysis.

---

# 13. Alert Closure

Before closing the alert, verify that:

- Investigation steps are complete
- Evidence is documented
- IOC handling is complete
- Scope is understood
- Containment is complete where required
- Escalation has been performed where required
- Verdict is justified
- Analyst note is complete

Closed alerts should remain useful for future investigations, detection tuning, threat-hunting pivots, incident review, analyst training, and repeat-attack correlation.

---

# 14. Detection Improvement

An investigation should end with one additional question:

> How could this activity be detected more reliably next time?

Consider:

- Did the rule fire too early?
- Did the rule miss stronger indicators?
- Was there an obvious false-positive pattern?
- Could correlation improve confidence?
- Could endpoint telemetry improve context?
- Could frequency thresholds be tuned?
- Could the detection incorporate allowlists or known-good context?

A detection improvement should document:

- Detection hypothesis
- Required telemetry
- Detection logic
- Potential false positives
- Tuning considerations
- Expected analyst response

---

# Analyst Decision Framework

A practical mental model for most SIEM alerts:

```text
1. Why did this alert fire?
2. What evidence directly supports the alert?
3. Is the activity malicious?
4. Did it succeed?
5. What systems or users are affected?
6. Is containment required?
7. Is escalation required?
8. What is the final verdict?
9. What should be detected better next time?
```

---

# Key SOC Principle

> An alert is not an incident until the evidence supports the conclusion.

The analyst's job is not to confirm the alert.

The analyst's job is to **test the alert hypothesis against available evidence**.

---

# Related Portfolio Areas

This workflow supports investigations involving:

- Phishing
- Malware
- Web attacks
- Network activity
- Endpoint compromise
- Authentication anomalies
- SIEM correlation
- Incident response

Related directories:

```text
investigations/
detection-engineering/
knowledge/
labs/
```

---

# Training Context

This reference was developed from hands-on SOC training and simulated investigations.

It has been rewritten as an analyst-focused operational reference rather than a training-platform walkthrough or answer guide.

All examples should be interpreted in the context of authorized lab and simulated environments.
