# Models and design decisions

This folder documents the analytical methods used in the prototype and the reasoning behind
them. The guiding principle is **explainability**: every model is a transparent, defensible
choice rather than a black box, because the system's job is to direct scarce analyst attention.

## Relevance filter (§6)

- **Method:** TF-IDF (uni- + bi-grams, sublinear TF) + Logistic Regression (`class_weight=balanced`).
- **Baseline:** keyword match against a hand-built cyber lexicon.
- **Evaluation:** stratified 5-fold cross-validation reporting precision / recall / F1.
- **Why:** interpretable (learned term weights are readable), trains in milliseconds, and is the
  right altitude for a prototype. **Production path:** a security-domain transformer (e.g. SecBERT)
  for semantic understanding of paraphrase.

## MITRE ATT&CK mapping (§8)

- **Method:** TF-IDF + cosine similarity between item text and technique descriptions; nearest
  technique assigned.
- **Why:** lightweight and explainable. **Production path:** embedding-based (sentence-transformer)
  matching for semantic rather than lexical alignment.

## Risk-scoring framework (§10)

A composite score in [0, 100] from five normalised, orthogonal factors:

| Factor | Source | Weight |
|--------|--------|:------:|
| Severity | CVSS base score | 0.30 |
| Exploitation status | CISA KEV listing + ransomware linkage | 0.25 |
| Exploit likelihood | EPSS probability | 0.20 |
| Corroboration | independent source count | 0.15 |
| Recency | exponential decay (half-life ~180 days) | 0.10 |

Tiers: Critical ≥ 70 · High 50–69 · Medium 30–49 · Low < 30. The weights are an explicit,
tunable **policy**, not a learned model — which is what makes each score auditable. A future
improvement is to calibrate the weights empirically against historical exploitation outcomes.

## Enrichment data sources

- **Severity (CVSS):** NVD API in production; bundled values in the offline snapshot.
- **Likelihood (EPSS):** FIRST EPSS API in production; bundled values in the offline snapshot.
