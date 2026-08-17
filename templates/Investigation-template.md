# SOC Investigation Report

## Case Information

| Field       | Details                     |
| ----------- | --------------------------- |
| Case ID     | SOC-XXX                     |
| Case Title  |                             |
| Analyst     |                             |
| Date        |                             |
| Environment | Authorized Lab / Simulation |
| Alert Type  |                             |
| Severity    |                             |
| Status      |                             |
| Verdict     |                             |
| Confidence  |                             |

---

# 1. Executive Summary

Provide a concise summary suitable for a SOC lead or incident-response manager.

Explain:

* What triggered the investigation
* What was discovered
* Whether the activity was malicious
* What systems or users were affected
* Whether containment or additional investigation is required

### Example structure

A security alert was generated after [brief description of suspicious activity].

Investigation of [relevant telemetry] identified [key findings].

The observed behavior was determined to be [true positive / false positive / benign positive] because [brief evidence].

The incident affected [scope], and the recommended response is [brief action].

---

# 2. Alert Information

| Field            | Value |
| ---------------- | ----- |
| Alert Name       |       |
| Detection Source |       |
| Timestamp        |       |
| Source IP        |       |
| Destination IP   |       |
| Source Host      |       |
| Destination Host |       |
| User             |       |
| Process          |       |
| File             |       |
| Initial Severity |       |

Include only fields relevant to the investigation.

---

# 3. Investigation Objective

Define what must be determined.

Examples:

* Determine whether the alert represents malicious activity.
* Identify the source and destination of the activity.
* Determine whether execution occurred.
* Identify affected users or endpoints.
* Determine whether additional systems were impacted.
* Identify indicators of compromise.
* Determine whether containment is required.

---

# 4. Initial Triage

Document what was known when the investigation began.

### Initial Observations

*
*
*

### Initial Hypotheses

**Hypothesis 1:**

**Hypothesis 2:**

**Hypothesis 3:**

Do not assume the alert is malicious before evidence supports that conclusion.

---

# 5. Evidence Collected

Document relevant evidence.

Possible evidence sources include:

* SIEM telemetry
* Windows Event Logs
* EDR telemetry
* Firewall logs
* DNS logs
* Proxy logs
* Web-server logs
* Authentication logs
* Email headers
* File metadata
* Process trees
* Network connections
* Threat-intelligence sources

---

# 6. Investigation

## 6.1 Investigation Step 1 — Initial Alert Analysis

### Question

What activity caused the alert?

### Analysis

Document the evidence examined.

### Findings

*
*
*

### Assessment

Explain what the evidence means.

---

## 6.2 Investigation Step 2 — Source Analysis

Investigate the originating:

* IP
* Host
* User
* Process
* Email sender
* Domain

depending on the case.

### Findings

*
*
*

---

## 6.3 Investigation Step 3 — Destination / Target Analysis

Determine what resource was targeted.

Possible targets:

* User account
* Endpoint
* Server
* Website
* Application
* Mailbox
* Network service

### Findings

*
*
*

---

## 6.4 Investigation Step 4 — IOC Enrichment

Investigate relevant indicators.

Possible tools:

* VirusTotal
* URLScan
* WHOIS
* AbuseIPDB
* MITRE ATT&CK
* Other appropriate threat-intelligence sources

### Important

Reputation results should support an investigation but should not automatically determine the verdict.

Correlate threat-intelligence findings with observed telemetry.

---

# 7. Indicators of Compromise

| Indicator | Type   | Context | Assessment |
| --------- | ------ | ------- | ---------- |
|           | IP     |         |            |
|           | Domain |         |            |
|           | URL    |         |            |
|           | SHA256 |         |            |
|           | Email  |         |            |

Possible assessments:

* Malicious
* Suspicious
* Benign
* Unknown

---

# 8. Timeline

| Time | Event | Evidence Source |
| ---- | ----- | --------------- |
|      |       |                 |
|      |       |                 |
|      |       |                 |
|      |       |                 |

Reconstruct the sequence of events whenever sufficient telemetry is available.

---

# 9. MITRE ATT&CK Mapping

| Tactic | Technique | Technique ID | Evidence |
| ------ | --------- | ------------ | -------- |
|        |           |              |          |
|        |           |              |          |

Only map techniques supported by observed evidence.

Do not add ATT&CK techniques solely because they are commonly associated with the malware or attack type.

---

# 10. Scope Assessment

## Users Affected

*

## Hosts Affected

*

## Accounts Affected

*

## Network Infrastructure Affected

*

## Additional Indicators Found

*

## Evidence of Lateral Movement

None observed / Observed / Unable to determine.

## Evidence of Persistence

None observed / Observed / Unable to determine.

## Evidence of Credential Compromise

None observed / Observed / Unable to determine.

---

# 11. Analysis & Verdict

## Verdict

**TRUE POSITIVE / FALSE POSITIVE / BENIGN POSITIVE**

## Confidence

**High / Medium / Low**

## Evidence Supporting Verdict

1.
2.
3.
4.

## Alternative Explanations Considered

Explain legitimate or benign explanations that were considered and why they were accepted or rejected.

---

# 12. Severity Assessment

**Severity:** Informational / Low / Medium / High / Critical

### Rationale

Consider:

* Asset criticality
* User impact
* Execution
* Credential compromise
* Privilege level
* Persistence
* Lateral movement
* Data exposure
* Command-and-control activity
* Number of affected systems

---

# 13. Containment Recommendations

Where appropriate:

* Block malicious IP/domain
* Isolate affected endpoint
* Disable compromised account
* Reset credentials
* Revoke sessions
* Remove malicious files
* Block malicious hashes
* Quarantine malicious emails
* Search environment for matching indicators

Only recommend actions justified by the findings.

---

# 14. Eradication & Recovery Recommendations

Potential actions:

* Remove persistence
* Delete malicious artifacts
* Patch exploited vulnerability
* Restore affected system
* Re-enable account after credential reset
* Validate host integrity
* Increase monitoring following remediation

---

# 15. Detection Opportunities

Ask:

> How could this activity be detected earlier or more reliably next time?

## Detection Hypothesis

Describe the behavior that should generate an alert.

---

## Splunk Detection

```spl
# Add SPL query here
```

### Detection Logic

Explain what the query identifies.

### Potential False Positives

*
*
*

### Tuning Considerations

*
*
*

---

## Sigma Rule

If appropriate:

```yaml
# Add Sigma rule here
```

---

## YARA Rule

If appropriate:

```yara
// Add YARA rule here
```

---

# 16. Lessons Learned

Document what the investigation taught you.

Examples:

* Which telemetry provided the strongest evidence?
* Which assumptions were incorrect?
* Which investigative pivot was most useful?
* What additional logging would improve visibility?
* Could the alert rule be improved?
* What would you investigate differently next time?

---

# 17. Tools Used

Examples:

* LetsDefend SIEM
* Splunk
* VirusTotal
* URLScan
* WHOIS
* AbuseIPDB
* MITRE ATT&CK
* CyberChef
* Wireshark
* Sysmon
* Windows Event Viewer

Only list tools actually used.

---

# 18. Evidence

Store sanitized screenshots in an `images/` directory inside the investigation folder.

Example:

```text
SOC-001-phishing-investigation/
│
├── README.md
└── images/
    ├── 01-alert.png
    ├── 02-header-analysis.png
    ├── 03-url-analysis.png
    └── 04-timeline.png
```

Reference them using:

```markdown
![SIEM Alert](images/01-alert.png)
```

Each image should support an analytical point rather than serving as decoration.

---

# 19. Analyst Conclusion

Conclude the case in one concise paragraph.

Summarize:

* What occurred
* The evidence supporting the conclusion
* Scope
* Final classification
* Required response

---

## Investigation Disclaimer

This investigation was conducted in an authorized lab or simulated SOC environment.

Sensitive information, challenge answers, flags, credentials, and unnecessary platform-specific information have been omitted or sanitized.

The purpose of this report is to demonstrate security-analysis methodology and incident-investigation skills.
