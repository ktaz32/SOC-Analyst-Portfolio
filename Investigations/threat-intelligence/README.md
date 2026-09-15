# Threat Intelligence Investigations

This directory contains SOC investigations where threat-intelligence indicators are the primary alert source or analytical pivot.

| Case | Investigation | Verdict | Key Skills |
|---|---|---|---|
| [SOC-018](./soc-018-threat-intel-url-tapscanner-false-positive/) | Threat-Intelligence URL Alert / TapScanner Redirect | False Positive | URL-shortener analysis, redirect validation, VirusTotal interpretation, shared-infrastructure reasoning, ATT&CK qualification |

## Analyst Principles

- Threat-intelligence matches are leads, not verdicts.
- Indicator freshness matters, especially for URLs.
- Shared services such as URL shorteners should not be blocklisted solely because one shortened URL appears in a feed.
- Resolve redirects and evaluate the final destination.
- Correlate CTI with event-time internal telemetry.
- Keep historical reputation separate from what was observed at the time of the alert.
