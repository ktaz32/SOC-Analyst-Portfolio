# Malicious Document Analysis — SOC Analyst Knowledge Base

## Purpose

This reference documents a practical workflow for analyzing suspicious Microsoft Office documents, with special emphasis on the **tools demonstrated during hands-on analysis**.

The workflow combines:

1. **Basic static analysis**
2. **Advanced Office/VBA analysis**
3. **Deobfuscation and IOC recovery**
4. **Sandbox / dynamic analysis**
5. **Threat-intelligence and PCAP enrichment**

The analyst's goal is to determine what the document does, what indicators it exposes, and what behavior can be confirmed.

---

# Tool Map

| Tool | Primary Use | Analyst Question |
|---|---|---|
| `file` | Validate real file type | Is the file what its extension claims? |
| ExifTool | Metadata analysis | What author/timestamp/document metadata exists? |
| `strings` | Printable-string extraction | Are URLs, commands, filenames, or scripts visible? |
| `grep` | Output filtering | Can I isolate `http`, `vbs`, `powershell`, `.exe`, etc.? |
| `olemeta` | OLE metadata | What Office/OLE metadata is embedded? |
| `oleid` | Office risk triage | Are VBA macros, encryption, or suspicious relationships present? |
| `olevba` | VBA extraction and analysis | What macros, auto-exec keywords, suspicious code, and IOCs exist? |
| Visual Studio Code | Manual VBA review | Can I trace variables and rebuild obfuscated strings? |
| ViperMonkey | VBA emulation | What actions/IOCs can be recovered without opening Office? |
| Hybrid Analysis | Automated sandbox | What processes, files, DNS, hosts, and payloads appear? |
| ANY.RUN | Interactive sandbox | What happens when the document executes? |
| CyberChef | Decode encoded content | What does Base64/encoded PowerShell resolve to? |
| VirusTotal | Reputation enrichment | Are recovered URLs/hashes known malicious? |
| Wireshark | PCAP analysis | What network traffic did the sample generate? |

---

# 1. Why Malicious Documents Matter

Microsoft Office documents can contain macros written in **Visual Basic for Applications (VBA)**. Attackers can abuse VBA to:

- auto-execute code;
- launch commands;
- invoke PowerShell;
- download payloads;
- write executables;
- use COM/WMI;
- contact external infrastructure.

A macro-enabled document is not automatically malicious. The analyst must examine the code and runtime behavior.

---

# 2. REMnux

The demonstrated static-analysis workflow uses **REMnux**.

REMnux provides command-line tooling for:

- metadata;
- strings;
- Office parsing;
- VBA extraction;
- deobfuscation;
- IOC recovery.

Use sandboxes such as Hybrid Analysis or ANY.RUN when runtime validation is required.

```text
REMnux
  ↓
Static / VBA analysis
  ↓
Recovered code + IOCs
  ↓
Sandbox
  ↓
Runtime validation
```

---

# 3. Basic Static Analysis Tools

## `file`

```bash
file suspicious.doc
```

Use it to validate the underlying file type.

## ExifTool

```bash
exiftool suspicious.doc
```

Useful metadata includes:

- author
- title
- creation time
- last saved time
- application/template data

## `strings`

```bash
strings suspicious.doc
```

Look for:

- URLs
- domains
- IPs
- `.exe`
- PowerShell
- VBS
- Temp/AppData paths

## `grep`

Examples:

```bash
strings suspicious.doc | grep -i http
strings suspicious.doc | grep -i powershell
strings suspicious.doc | grep -i vbs
strings suspicious.doc | grep -i exe
```

`grep` makes noisy string output useful by isolating specific pivots.

---

# 4. Oletools

## `olemeta`

```bash
olemeta suspicious.doc
```

Useful for Office/OLE metadata such as:

- template
- create time
- last save time
- page/word counts
- summary properties

## `oleid`

```bash
oleid suspicious.doc
```

Use it for quick Office risk triage:

- file format
- OLE container
- encryption
- VBA macro presence
- suspicious macro keywords
- external relationships

`oleid` answers:

> Do I need deeper VBA analysis?

## `olevba`

```bash
olevba suspicious.doc
```

This is the core VBA-analysis tool demonstrated.

It helps expose:

- VBA source
- auto-execution
- suspicious keywords
- possible IOCs
- obfuscation

High-value findings include:

```text
AutoOpen
Workbook_Open
Shell
Kill
GetObject
User-Agent
Chr
PowerShell
Base64
IP addresses
URLs
```

---

# 5. Understanding `olevba`

## Auto-Execution

```text
AutoOpen
Workbook_Open
```

These indicate macro code may execute when the document opens.

## Command Execution

```text
Shell
```

May run an executable or system command.

## File Deletion

```text
Kill
```

May delete a file.

## Obfuscation

```text
Chr(...)
```

The course demonstrates strings split through:

- `+`
- `&`
- quotation marks
- `Chr()` values

Example:

```text
"cr" + "eate" + "object"
```

becomes:

```text
createobject
```

---

# 6. Manual Deobfuscation

Use Visual Studio Code to:

- search variables;
- find assignments;
- replace obfuscated values;
- reconstruct URLs;
- reconstruct filenames;
- rebuild payload paths.

Example concept:

```text
"C:\Users\User\AppData\Local\Temp\" + "444." + Chr(101) + "xe"
```

resolves to:

```text
C:\Users\User\AppData\Local\Temp\444.exe
```

Useful workflow:

```text
Find suspicious variable
        ↓
Find assignment
        ↓
Resolve fragments
        ↓
Replace references
        ↓
Rebuild final IOC
```

---

# 7. `olevba` Deobfuscation

The demonstrated workflow exports VBA and then deobfuscates it.

```text
Document
   ↓
olevba extraction
   ↓
baddoc.vba
   ↓
olevba deobfuscation
   ↓
clearer VBA
```

Deobfuscated code exposed indicators such as:

- PowerShell
- `ExecutionPolicy Bypass`
- `NoProfile`
- `System.Net.WebClient`
- `DownloadFile`
- `cmd.exe`
- Temp paths
- executable filenames
- URLs

This is where static analysis begins to reveal the attack chain.

---

# 8. Visual Studio Code

Visual Studio Code is useful after extraction because it provides:

- syntax highlighting;
- search;
- find/replace;
- variable tracing;
- easier manual reconstruction.

A practical analyst workflow:

```text
olevba output
    ↓
VS Code
    ↓
Find suspicious variable
    ↓
Trace value
    ↓
Reconstruct command / URL
```

---

# 9. ViperMonkey

ViperMonkey is demonstrated as a VBA emulation tool.

Conceptual command:

```bash
vmonkey extracted.vba
```

IOC-oriented use:

```bash
vmonkey --iocs extracted.vba
```

It can help recover actions such as:

- delete file
- execute command
- drop file
- get object
- query WMI
- hashes
- parameters

The demonstrated workflow removes non-VBA text before running ViperMonkey.

### SOC value

ViperMonkey helps bridge:

```text
static source
```

and:

```text
behavior
```

without directly opening the malicious document in Office.

---

# 10. PowerShell Indicators

High-value PowerShell findings demonstrated include:

```text
PowerShell
-W Hidden
-enc
-NoProfile
ExecutionPolicy Bypass
System.Net.WebClient
DownloadFile
Start-Sleep
cmd.exe
```

The strongest signal is the combination:

```text
Office macro
+
PowerShell
+
bypass / hidden
+
download
+
executable
+
Temp
```

---

# 11. Hybrid Analysis

Hybrid Analysis is demonstrated as a **non-interactive sandbox**.

Useful output includes:

- malicious/suspicious verdicts;
- AV detections;
- process tree;
- DNS requests;
- contacted hosts;
- HTTP activity;
- extracted strings;
- extracted files;
- ATT&CK mappings.

A demonstrated chain looked like:

```text
Word document
      ↓
PowerShell
      ↓
downloaded executable
```

Do not stop at the verdict. Review the process tree and extracted behavior.

---

# 12. ANY.RUN

ANY.RUN is demonstrated as an **interactive sandbox**.

Useful views include:

- live processes;
- process graph;
- HTTP requests;
- connections;
- DNS;
- IOCs;
- ATT&CK matrix;
- command lines;
- text report;
- downloadable PCAP.

Workflow:

```text
Upload document
   ↓
Start sandbox
   ↓
Observe execution
   ↓
Review process graph
   ↓
Review DNS/HTTP/connections
   ↓
Extract IOCs
   ↓
Download PCAP if needed
```

---

# 13. Process Graph Analysis

A high-value pattern demonstrated is:

```text
WINWORD.EXE
     ↓
powershell.exe
     ↓
downloaded executable
```

Process ancestry matters.

```text
powershell.exe
```

alone may be normal.

But:

```text
WINWORD.EXE
   ↓
powershell.exe -W Hidden -enc ...
```

is much more suspicious.

---

# 14. CyberChef

CyberChef is demonstrated for decoding encoded PowerShell copied from sandbox command lines.

Workflow:

```text
Copy encoded PowerShell
        ↓
CyberChef
        ↓
From Base64
        ↓
Remove Null Bytes if needed
        ↓
Extract URLs / commands
```

Useful operations:

- From Base64
- Remove Null Bytes
- Extract URLs

Encoding itself is not malicious; context determines significance.

---

# 15. VirusTotal

Use VirusTotal to enrich recovered:

- hashes
- URLs
- domains
- IPs
- secondary payloads

Example:

```text
Recovered URL
   ↓
VirusTotal
   ↓
Reputation
   ↓
Record as supporting evidence
```

Do not treat reputation as the only evidence.

---

# 16. Wireshark

ANY.RUN can provide PCAP files for sandbox executions.

Use Wireshark to answer:

- What DNS requests occurred?
- What IPs were contacted?
- What ports were used?
- Was HTTP visible?
- Was a payload transferred?
- Did sandbox traffic match static IOCs?

This creates a strong correlation chain:

```text
Static IOC
   ↓
Sandbox execution
   ↓
PCAP
   ↓
Network validation
```

---

# 17. Recommended Workflow

## Phase 1 — Basic Triage

```bash
file suspicious.doc
exiftool suspicious.doc
strings suspicious.doc
```

Filter:

```bash
strings suspicious.doc | grep -i http
strings suspicious.doc | grep -i powershell
strings suspicious.doc | grep -i exe
```

## Phase 2 — Office-Specific Analysis

```bash
olemeta suspicious.doc
oleid suspicious.doc
olevba suspicious.doc
```

Questions:

```text
Macros?
Auto-exec?
Obfuscation?
URLs?
PowerShell?
Payload paths?
```

## Phase 3 — Deobfuscation

- export VBA;
- inspect in VS Code;
- trace variables;
- rebuild strings;
- recover IOCs.

## Phase 4 — VBA Emulation

Use ViperMonkey for behavioral recovery.

## Phase 5 — Sandbox

Use Hybrid Analysis and/or ANY.RUN.

Review:

```text
process tree
command lines
DNS
HTTP
connections
extracted files
payloads
```

## Phase 6 — Decode Secondary Content

Use CyberChef for encoded PowerShell.

## Phase 7 — Enrichment

Use VirusTotal.

## Phase 8 — Network Validation

Download PCAP and review with Wireshark where useful.

---

# 18. High-Value Indicators

## VBA

```text
AutoOpen
Workbook_Open
CreateObject
Shell
Kill
GetObject
Chr
WScript
PowerShell
cmd.exe
```

## PowerShell

```text
-enc
-EncodedCommand
-W Hidden
-NoProfile
ExecutionPolicy Bypass
System.Net.WebClient
DownloadFile
```

## Paths

```text
%TEMP%
%APPDATA%
C:\Windows\Temp
```

## Network

```text
http://
https://
IP addresses
domains
user-agent strings
```

---

# 19. ATT&CK Mapping Examples

Only map behavior supported by evidence.

| Behavior | ATT&CK |
|---|---|
| Malicious document opened | `T1204.002` |
| PowerShell | `T1059.001` |
| WMI | `T1047` |
| Obfuscation | `T1027` |
| Secondary payload download | `T1105` |
| Phishing attachment | `T1566.001` only when delivery evidence exists |

Do not infer phishing if all you have is the document sample.

---

# 20. Analyst Decision Points

## Does the document contain macros?

Use:

```text
oleid
olevba
```

## Does it auto-execute?

Look for:

```text
AutoOpen
Workbook_Open
```

## Is it obfuscated?

Look for:

```text
Chr()
concatenation
split strings
encoded PowerShell
```

## Does it download a payload?

Look for:

```text
WebClient
DownloadFile
ServerXMLHTTP
URLs
```

## Did the payload execute?

Static analysis may not prove execution.

Use sandbox process telemetry.

## Is an extracted URL definitely C2?

No. It may be:

- payload hosting;
- redirect infrastructure;
- telemetry;
- C2.

Describe only what the evidence supports.

---

# 21. Common Mistakes

Avoid:

- opening suspicious documents on a normal workstation;
- enabling macros outside a controlled environment;
- trusting antivirus reputation alone;
- treating every URL as C2;
- treating all PowerShell as malicious;
- assuming encoded content is automatically malicious;
- copying sandbox ATT&CK tags without validating behavior;
- ignoring process ancestry;
- ignoring encoded command lines;
- failing to distinguish extracted IOCs from enterprise-observed IOCs.

---

# 22. Quick Tool Reference

```text
file
→ file type

ExifTool
→ metadata

strings
→ printable strings

grep
→ focused string search

olemeta
→ OLE metadata

oleid
→ Office risk triage

olevba
→ VBA extraction + suspicious keywords + IOCs

Visual Studio Code
→ manual VBA tracing

ViperMonkey
→ VBA emulation / IOC recovery

Hybrid Analysis
→ automated sandbox

ANY.RUN
→ interactive sandbox

CyberChef
→ decode scripts / PowerShell

VirusTotal
→ IOC enrichment

Wireshark
→ PCAP validation
```

---

# 23. Detection Opportunities

## Office → PowerShell

```text
WINWORD.EXE / EXCEL.EXE
        ↓
powershell.exe
```

Increase severity with:

```text
-enc
-W Hidden
-NoProfile
ExecutionPolicy Bypass
```

## Office → Network → Executable

```text
Office
+
outbound network
+
executable written to Temp
```

## Macro Downloader Pattern

```text
AutoOpen
+
CreateObject
+
ServerXMLHTTP / WebClient
+
ADODB.Stream
+
.exe
```

## Encoded PowerShell

```text
Office parent
+
PowerShell
+
EncodedCommand
+
network activity
```

---

# 24. Reporting Template

```text
Executive Summary
Sample Information
File Type / Metadata
Macro Presence
Auto-Execution
Static Findings
Obfuscation
Deobfuscation
Recovered Commands
Recovered IOCs
Sandbox Process Tree
Network Activity
Dropped / Downloaded Files
MITRE ATT&CK
Evidence vs Inference
Verdict + Confidence
Detection Opportunities
Response Recommendations
```

---

# SOC Takeaway

The strongest malicious-document analysis combines tools:

```text
file / ExifTool / strings
        ↓
olemeta / oleid
        ↓
olevba
        ↓
Visual Studio Code
        ↓
ViperMonkey
        ↓
Hybrid Analysis / ANY.RUN
        ↓
CyberChef
        ↓
VirusTotal
        ↓
Wireshark
        ↓
Evidence-based verdict
```

The important skill is knowing **which tool answers which investigative question** and how to correlate the results into a defensible narrative.

---

# Training Context

This knowledge base was created from authorized malicious-document-analysis training material and is intended for defensive security education and SOC portfolio use.

Suspicious documents should only be analyzed in controlled environments designed for malware research.
