# Bundled data snapshot

This folder holds the deterministic, factually-grounded snapshot the notebook uses when
`USE_LIVE_DATA = False`. It makes every result in the notebook reproducible and lets the
pipeline run offline (e.g. without internet access in a demo).

| File | Contents | Schema |
|------|----------|--------|
| `sample_kev.json` | Real CISA KEV entries (condensed) | `cve, vendor, product, vuln_name, date_added, cwe, ransomware, cvss_base, epss` |
| `sample_news.json` | Security-news / OSINT items (cyber + deliberate noise) | `title, source, published, summary` |
| `sample_attack.json` | MITRE ATT&CK technique extract | `technique_id, technique_name, description` |

Provenance notes:

- The CVEs and their vendor/product/weakness metadata are **genuine** CISA KEV entries; the
  ATT&CK techniques are **genuine** framework entries.
- `cvss_base` (severity) and `epss` (exploit probability) are **bundled demo stand-ins** — CISA
  KEV does not publish them. In production they are fetched live from the NVD and FIRST APIs
  (the call sites are marked in §7 of the notebook).
- In Google Colab the notebook instead pulls these feeds **live**, so this snapshot is only the
  offline / reproducible fallback.
