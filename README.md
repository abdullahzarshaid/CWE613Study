# Logout Is Not Expiration — A Source-Aware Semantic Characterization of CWE-613

Research materials accompanying the manuscript **"Logout Is Not Expiration: A Source-Aware
Semantic Characterization of CWE-613."**

**Authors:** Abdullah Bin Zarshaid, Shahbaz Akhtar Siddiqui
**Status:** Manuscript prepared for submission to *IEEE Access* (not yet peer-reviewed or published).

---

## The problem in one paragraph

A web vulnerability labelled **CWE-613 (Insufficient Session Expiration)** can actually describe three
*different* lifecycle failures: a **logout** that does not terminate the session, an **authority
revocation** that is not enforced, or a **timeout** that never expires. The single shared label does not
say which condition failed — so "CWE-613" quietly conflates behaviours that require *different* tests.
This study measures how often each meaning appears and gives evidence-linked coding rules and executable
examples of the distinct checks.

## What the study does

- **A frozen corpus of 609 CWE-613 records** from the U.S. National Vulnerability Database (annual JSON
  feeds collected in September 2026, publication window from 2017), with cryptographic hashes over the
  exact record text for provenance.
- **Source-aware semantic coding** of each record's lifecycle event, authority-bearing object, scope and
  subsequent operation — with a description-only baseline and a reviewed version.
- **A synthetic HTTP laboratory ("SessTrace")** — six event-driven and two time-driven witnesses (399
  recorded HTTP steps) that illustrate the *different* test each lifecycle condition requires.
- **Neighbouring-CWE and catalogue-history analysis** (CWE-672 and CWE-384 records, plus CWE-613's own
  versioned history) to explain the interpretation boundaries.

## Headline measurements (stated honestly)

- **22.00%** of records (134/609) map to **explicit session termination**.
- The **combined termination-and-withdrawal** share is **280/609 (45.98%)** — and, importantly, this is
  **not** a measure of "logout failures" alone.
- Under recorded alternative interpretations the combined share ranges **37.44%–55.99%**, which supports a
  **substantial event-driven component but not a robust majority claim.**
- Repeat-coding reliability on a 120-record archived comparison: **118/120 agreement, Cohen's κ = 0.979.**

The paper deliberately avoids over-claiming: it documents the *plurality of meanings* inside CWE-613 and
provides the evidence trail, rather than asserting a single dominant cause.

## Reproducibility

The accompanying `Supplement.zip` contains the retained data, analysis code, figure sources, evidence map
and the SessTrace laboratory. Reproduction uses **Python 3.11+ and the standard library** (plotting needs
Matplotlib/NumPy); it makes **no AI-service calls, downloads no new data, and needs no API key**:

```bash
# after extracting Supplement.zip, from the Supplement/ folder:
python -m pip install -r analysis/requirements.txt
python analysis/reproduce.py --verify-only   # check the retained files
python analysis/reproduce.py                  # reproduce the measurements
python analysis/reproduce.py --verify-only    # verify again
```

A successful run prints `PASS`: it checks the 609 records, compares 61 reference result files, regenerates
the figures, and runs the retained research and software tests. Read `Supplement/Methods.txt` for evidence
conditions and limitations, and `Supplement/dataset/Codebook.txt` for the coding rules.

## Research integrity

- **Methods and limitations are documented up front** (`Supplement/Methods.txt`): the coding is not a
  preregistered blind protocol, the workflow batches are not independent raters, and the human
  cross-check is author-reported. These caveats are stated in the package itself.
- **AI-assistance disclosure:** as recorded in the manuscript's acknowledgment, AI coding assistants
  supported literature triage, editing, and analysis/figure/software work; final classification decisions,
  the analyses, and responsibility for the manuscript remain the authors'. Disclosing this is required
  academic practice and is retained deliberately.

## Rights and reuse — please read before redistributing

**`Supplement.zip` is a scholarly peer-review package, not an open-source or Creative Commons release.**
It bundles content whose rights remain with their holders — including MITRE/CWE catalogue content (under
MITRE's notice), NVD record text, and IEEE publisher template assets. Per `Supplement/evidence/Rights.txt`:

- Inclusion here grants **no** blanket licence. A source URL or hash grants no licence to the linked content.
- **Public redistribution of the package contents requires the rights holders' authorization and a
  specific author-approved licence**, which is pending.
- Original analysis code and annotations are the authors' work; a licence for them will be applied on
  formal release.

Until then, please use the materials for scholarly inspection and cite the manuscript rather than
re-hosting the contents.

## Citation

If you reference this work, please cite the manuscript:

> A. Bin Zarshaid and S. A. Siddiqui, "Logout Is Not Expiration: A Source-Aware Semantic Characterization
> of CWE-613," manuscript prepared for submission to IEEE Access, 2026.
