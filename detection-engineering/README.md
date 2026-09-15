# Detection Engineering

This directory contains investigation-derived detection notes and serves as the bridge between SOC analysis and reusable detection logic.

The guiding question is:

> **How could this behavior be detected reliably, tested against benign activity, and tuned for a production SOC?**

---

# Detection Engineering Approach

A detection should document:

1. Threat behavior
2. Required telemetry
3. Detection hypothesis
4. Detection logic
5. Positive test case
6. Negative / benign test case
7. False-positive considerations
8. Tuning boundaries
9. MITRE ATT&CK mapping
10. Analyst response / investigation steps

```text
Investigation finding
        ↓
Behavior abstraction
        ↓
Telemetry selection
        ↓
Detection logic
        ↓
Positive + negative testing
        ↓
Tuning
        ↓
Analyst playbook
```

---

# Current Investigation-Derived Detection Areas

Current portfolio work has generated detection ideas for:

- malicious-domain and malicious-URL access
- threat-intelligence feed confidence and IOC expiration
- URL-shortener redirect resolution
- password-protected attachment risk
- Office → suspicious child process
- Office → PowerShell / remote file download
- Office → outbound infrastructure
- SQL injection
- XSS
- IDOR enumeration
- command injection
- credential-file access
- HTTP Basic Authentication over plaintext
- AppData executable creation
- Run-key persistence
- direct SMTP from unusual processes
- ransomware recovery inhibition
- repeated Windows 4625 failures followed by 4624 success
- password-spraying / brute-force distribution patterns
- legitimate-installer false-positive reduction
- shared-infrastructure false-positive reduction

---

# Detection Quality Principles

A detection should be:

- **behavior-based** where possible
- **telemetry-aware**
- **testable**
- **explainable to an analyst**
- **tuned against benign behavior**
- **mapped to ATT&CK only when supported**

Important distinctions:

```text
IOC match ≠ compromise
sandbox capability ≠ endpoint execution
reputation score ≠ verdict
failed logons ≠ brute force by themselves
```

---

# Standalone Detection-as-Code Project

For the full engineering implementation, see:

**[Detection-as-Code Pipeline](https://github.com/ktaz32/Detection-as-Code-Pipeline)**

That project includes:

- Sigma detections
- Python validation
- positive and negative behavioral fixtures
- GitHub Actions CI
- single-event and multi-event correlation logic
- MITRE ATT&CK mapping
- analyst playbooks
- false-positive analysis
- reproducible test execution

The standalone repository is intentionally kept separate so this SOC portfolio can focus on **investigations**, while the Detection-as-Code project demonstrates **engineering and automated validation**.

---

# Current / Developing Technologies

- Sigma
- Python
- GitHub Actions
- Windows Security Event telemetry
- Sysmon
- correlation detections
- analyst playbooks
- Splunk SPL
- YARA

The emphasis is on detections that are **explainable, evidence-driven, and testable**, rather than collections of unvalidated rules.
