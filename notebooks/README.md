# Notebooks

## `OSINT_Threat_Monitoring_Prototype.ipynb`

The primary deliverable: a self-contained, teaching-style implementation of the full OSINT
threat-monitoring pipeline — **collect → filter → enrich → cluster → score → rank → report**.

Every stage produces visible output, so the logic can be inspected and defended step by step:

- **§1–2** Problem motivation and system architecture
- **§3–4** Environment setup and live data acquisition (CISA KEV, Google News RSS, MITRE ATT&CK)
- **§5** Exploratory data analysis (Figures 1–3)
- **§6** Relevance filtering: TF-IDF + Logistic Regression vs a keyword baseline, evaluated by
  5-fold cross-validation (Figure 4)
- **§7–8** Enrichment (IOC extraction, KEV join, CVSS/EPSS) and MITRE ATT&CK mapping (Figure 5)
- **§9** Clustering / de-duplication and source corroboration (Figure 6)
- **§10** Transparent 5-factor risk-scoring framework with a fully worked calculation
- **§11–12** Ranked risk register, visualisations (Figures 7–9) and a generated threat report
- **§13–15** Discussion (data quality, ethics/legal, scalability), conclusion and references

### How to run

- **Google Colab (live):** open the notebook, set `USE_LIVE_DATA = True`, and run all. It
  fetches the live CISA KEV catalogue and Google News RSS, so numbers reflect the current day.
- **Offline / deterministic:** leave `USE_LIVE_DATA = False`. The notebook uses the bundled
  snapshot in [`../data_sample/`](../data_sample/); all committed outputs were produced this way.

The only non-standard dependency is `feedparser` (installed in the first code cell).
