# Plots

The notebook generates and saves nine figures here when run (`fig1_*.png` … `fig9_*.png`).

> **Note:** this folder is git-ignored, so the PNGs are not committed. The same figures are
> **embedded directly in the executed notebook**, so they are visible on GitHub without rerunning
> anything — open [`../notebooks/OSINT_Threat_Monitoring_Prototype.ipynb`](../notebooks/OSINT_Threat_Monitoring_Prototype.ipynb).

Figures produced:

1. Exploited-vulnerability timeline and top vendors (EDA)
2. Weakness types (CWE) and CVSS severity distribution (EDA)
3. OSINT news feed composition (EDA)
4. Relevance filter — confusion matrix and benchmark vs keyword baseline
5. Candidates mapped to MITRE ATT&CK techniques
6. Source corroboration per vulnerability
7. Risk-score distribution and tier breakdown
8. Top 10 vulnerabilities by composite risk score
9. Risk-score decomposition (factor contributions) for the top vulnerabilities
