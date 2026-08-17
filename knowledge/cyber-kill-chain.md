# Cyber Kill Chain — SOC Analyst Notes

## What I Learned

The Cyber Kill Chain is a framework developed by Lockheed Martin to model the sequence of attacker activity across a cyber attack.

The model contains seven stages:

1. Reconnaissance
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command and Control (C2)
7. Actions on Objectives

From a SOC perspective, the value of the model is not only in naming attack stages, but in understanding:

* What the attacker has already achieved
* What evidence may exist from earlier stages
* What activity may happen next
* Where defenders can interrupt the attack

---

# 1. Reconnaissance

Reconnaissance is the information-gathering stage.

I learned that reconnaissance can be divided into:

## Passive Reconnaissance

Information is gathered without directly interacting with the target.

Examples:

* Public websites
* Social media
* Open-source information
* Employee email addresses
* Vendor relationships
* Archived websites

## Active Reconnaissance

The attacker directly interacts with the target.

Examples:

* Port scanning
* Service enumeration
* Detecting internet-facing systems
* Identifying software versions
* Finding exposed vulnerabilities

### SOC Perspective

Reconnaissance may be difficult to detect, especially when it is passive.

Potential defensive actions include:

* Monitoring internet-facing assets
* Identifying unnecessary public information exposure
* Threat-intelligence monitoring
* External penetration testing
* Keeping public-facing systems patched

---

# 2. Weaponization

Weaponization is where the attacker prepares the tools or malicious content required for the attack.

Examples I studied included:

* Creating malware
* Developing exploits
* Creating phishing templates
* Creating malicious documents
* Selecting appropriate attack tools

A useful example from the training involved creating:

* A phishing email template
* A malicious Word document containing macro code

These actions were part of the weaponization stage because the attack material was being prepared before delivery.

### SOC Perspective

This phase mostly occurs outside the victim environment.

Defenders may not directly observe weaponization, but they can:

* Track known attack tools
* Monitor threat intelligence
* Patch known vulnerabilities
* Prepare detection rules for known techniques

---

# 3. Delivery

Delivery is the point where malicious content reaches the target.

Examples include:

* Phishing emails
* Malicious attachments
* Malicious URLs
* Malware delivered through websites
* Malicious content delivered through social media
* Malware delivered through USB devices

One training scenario involved malware being placed on multiple USB drives and intentionally left near the target organization.

This was an important example because delivery does not always occur through email or the internet.

### Key Distinction

**Delivery means the payload reaches the victim.**

Execution has not necessarily occurred yet.

### SOC Perspective

Potential data sources include:

* Email gateway logs
* Proxy logs
* Web logs
* Firewall logs
* USB/device-control telemetry
* Endpoint security products

---

# 4. Exploitation

Exploitation is where the malicious content or exploit actually executes.

Examples:

* Running malware
* Executing a malicious macro
* Exploiting a software vulnerability
* Exploiting an operating-system vulnerability

### Key Distinction

**Delivery = payload arrives.
Exploitation = payload executes.**

This distinction is important.

A delivered malicious file that is never executed means the attack may have been stopped before successful exploitation.

### SOC Perspective

Useful telemetry includes:

* EDR
* Process execution logs
* Windows Event Logs
* Script execution logs
* Application logs
* Vulnerability/exploit detections

---

# 5. Installation

Installation is where the attacker attempts to establish persistence or additional malicious capability on the compromised system.

Examples I studied included:

* Installing malware
* Installing a backdoor
* Creating a web shell
* Creating a scheduled task
* Adding services
* Modifying firewall rules
* Privilege escalation to support persistence

One training scenario involved an attacker creating a suspicious scheduled task after gaining access.

The EDR detected the scheduled task, allowing the SOC analyst to investigate and stop the attack before later stages.

### SOC Perspective

Important evidence may include:

* Scheduled tasks
* New services
* Registry changes
* Startup modifications
* New executable files
* Process activity
* Configuration changes

Useful controls include:

* EDR
* Threat hunting
* Application control
* Least privilege
* Network security monitoring

---

# 6. Command and Control (C2)

Command and Control is where the compromised system communicates with attacker-controlled infrastructure.

At this stage, the attacker can establish remote communication and issue commands.

Examples include:

* Victim connecting to a malicious external IP
* Reverse connections
* Malware beaconing
* Remote-command infrastructure

### Important Point

C2 communication does not necessarily mean the attacker's final objective has already been completed.

It means the attacker has established a communication channel and is positioned to continue the attack.

### SOC Perspective

Potential indicators include:

* Suspicious outbound connections
* Known malicious IP addresses
* Unusual DNS activity
* Repeated beaconing
* Connections to known C2 infrastructure

Useful controls include:

* Firewall rules
* Network security monitoring
* Threat intelligence
* DNS monitoring
* EDR network telemetry

---

# 7. Actions on Objectives

Actions on Objectives is the final stage.

This is where the attacker carries out the intended goal of the attack.

Examples studied included:

* Encrypting files with ransomware
* Exfiltrating sensitive information
* Deleting critical information
* Collecting credentials
* Privilege escalation
* Expanding access to additional systems
* Manipulating system information

A training example referenced data deletion using SDelete as activity belonging to this final stage.

### SOC Perspective

At this stage, the SOC must focus heavily on impact and scope.

Important questions include:

* Was data stolen?
* Were files encrypted?
* Were systems damaged?
* Were credentials compromised?
* Did the attacker access other systems?
* What must be contained immediately?

Defensive controls may include:

* DLP
* Network monitoring
* Access control
* Database monitoring
* Identity monitoring
* Incident response

---

# Attack Chain Example

One scenario from the training showed the following sequence:

```text
Reconnaissance
↓
Target and technology information gathered

Weaponization
↓
Malware embedded into a legitimate executable

Delivery
↓
Malware placed on USB devices

Exploitation
↓
User executes the malicious program

Installation
↓
Scheduled task created for persistence

Command and Control
↓
Reverse connection allows remote commands

Actions on Objectives
↓
Further attacker objectives would follow if not stopped
```

This scenario helped show that the Cyber Kill Chain is not just theoretical; each stage can correspond to observable attacker activity.

---

# SOC Analyst Takeaway

The biggest lesson I learned is that a SOC analyst should not stop at the alert that triggered the investigation.

If an alert appears to show activity from one stage of the Kill Chain, the analyst should investigate both:

**Backward:**
What happened before this?

**Forward:**
What may have happened after this?

For example:

```text
Suspicious scheduled task detected
        ↓
Installation
        ↓
How was the system initially compromised?
        ↓
Was malware delivered?
        ↓
Was it executed?
        ↓
Did the host establish C2?
        ↓
Did the attacker achieve any objectives?
```

This is how the Cyber Kill Chain becomes useful during real SOC investigations.

---

# Quick Reference

| Stage                 | Core Question                                            |
| --------------------- | -------------------------------------------------------- |
| Reconnaissance        | What information did the attacker gather?                |
| Weaponization         | What attack tool or payload was prepared?                |
| Delivery              | How did the payload reach the victim?                    |
| Exploitation          | Did the malicious content execute?                       |
| Installation          | Was persistence or malware installed?                    |
| Command & Control     | Did the victim communicate with attacker infrastructure? |
| Actions on Objectives | What final impact or objective was achieved?             |

---

# Training Outcome

After completing this module, I am able to:

* Identify the seven Cyber Kill Chain stages
* Distinguish passive and active reconnaissance
* Separate Delivery from Exploitation
* Identify persistence activity as Installation
* Recognize suspicious outbound communication as potential C2
* Identify attacker impact as Actions on Objectives
* Use the Kill Chain to guide the next steps of an investigation
