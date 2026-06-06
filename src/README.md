# Source package (next phase)

This directory is reserved for the modular Python package that will refactor the notebook's
validated logic into reusable components. The current deliverable is the notebook in
[`../notebooks/`](../notebooks/); this package is the planned next step.

Intended modules (mirroring the notebook's pipeline stages):

- **collect** — source connectors (CISA KEV, news/RSS, MITRE ATT&CK) with scheduling and back-off
- **filter** — the relevance classifier and its training/evaluation utilities
- **enrich** — IOC extraction, KEV join, live CVSS (NVD) and EPSS (FIRST) enrichment
- **map** — MITRE ATT&CK technique alignment
- **cluster** — per-CVE de-duplication and source corroboration
- **score** — the weighted risk-scoring framework
- **report** — risk-register and threat-report generation

Separating the package from the notebook follows standard research-engineering practice:
the notebook tells the linear story; the package makes the same logic reusable and testable.
