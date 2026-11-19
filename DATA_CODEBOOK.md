# NATO/EU Defense YouTube Comments Corpus
## Data Codebook
### Documentation of an Empirically Validated Social Text Dataset

**Author:** Balázs Meczkó  
**Affiliation:** Bibó István Szakkollégium · Kutatószeminárium: *Mesterséges intelligencia a társadalom- és politikatudományi kutatásban* (2026. ősz)  
**Instructor:** Miklós Sebők (poltextLAB / CEU Democracy Institute)  
**Date:** 2026. november 17.  
**Version:** 1.0  
**Licence:** Creative Commons Attribution 4.0 International (CC-BY 4.0)  
**Repository:** `https://github.com/kockabalazs-arch/my-agent-skills` / `bibo-disinfo-youtube`

---

## 1. Introduction

Online video platforms, particularly YouTube, have emerged as primary battlegrounds for cognitive warfare, state-sponsored disinformation campaigns, and hybrid influence operations. While institutional actors (NATO, the European Union, and member state governments) increasingly communicate their security and defense policy through digital video formats, the comment sections beneath these videos function as accessible targets for coordinated amplification, public opinion manipulation, and troll network deployment.

Conducting rigorous computational and qualitative text analysis on digital disinformation requires structured, comprehensive, and empirically validated text corpora. The **NATO/EU Defense YouTube Comments Corpus** was constructed to capture user-level reactions, rhetorical strategies, and potential state-backed narrative patterns surrounding key European defense events in late 2026. 

This data codebook provides comprehensive documentation for potential researchers and peer evaluators, adhering to the standardized **ParlLawSpeech (PLS)** data documentation template (Schwalbach, Hetzer, Proksch, Rauh & Sebők, 2025). It describes the scope and coverage, collection methodology, data schema and variables (with a strict core-versus-additional partition), the 5-step data validation workflow, and licensing details.

---

## 2. Coverage and Data Collection

### 2.1 Case Selection Rationale
The corpus is focused on three high-reach international news and geopolitical analysis videos that address core dilemmas of European collective security and the Russia–Ukraine war. The selection rationales were:
1. **High public engagement and exposure:** Videos with hundreds of thousands of views that attracted hundreds to thousands of user comments within days of publication.
2. **Topical diversity across defense dimensions:**
   - *Conventional/military deterrence and escalation threat:* Germany’s intelligence warning of potential direct military confrontation.
   - *Sub-threshold and asymmetric warfare:* Explanations of Russian hybrid tactics, sabotage, and cyber interference across Europe.
   - *Economic warfare and sanction circumvention:* Investigative reporting on the circumvention of Western oil/diesel sanctions.
3. **Low moderation bias:** Unfiltered public comment sections where bot activity, organized narrative seeding, and authentic user debate coexist without heavy censorship.

### 2.2 Data Collection
Data collection was executed on **2026. október 11.** using the cloud-based **Apify YouTube Comment Scraper** tool. The scraper retrieved full comment text payloads, thread parent-child links, engagement metrics (upvotes, reply counts), and author identifiers directly from the YouTube InnerTube API.

#### Table 1: Descriptive Statistics of the Target Video Corpora
*Data on YouTube video comments collected on 2026-10-11*

| Video ID | Channel / Outlet | Video Title | Comment Count ($N$) | Share (%) | Time Frame |
| :--- | :--- | :--- | :---: | :---: | :--- |
| `zv9qWicFwUs` | DW News | *How Russia turned sanctions into a diesel deal* | 1,102 | 46.48% | Oct 2026 |
| `SOrsv4KfeaY` | Good Times Bad Times | *Why Russia’s Hybrid War Doesn’t Feel so Hybrid* | 711 | 29.99% | Oct 2026 |
| `T5_tLTGz-Xs` | DW News | *Germany's spy chief warns risk of 'violent conflict' with Russia* | 558 | 23.53% | Oct 2026 |
| **Total** | **3 Videos** | **Complete Validated Corpus** | **2,371** | **100.00%** | **Oct 2026** |

---

## 3. Data Structure and Variables

The validated corpus is distributed as a comma-separated values file (`comments_clean.csv`), encoded in **UTF-8** without Byte Order Mark (BOM). In compliance with the ParlLawSpeech documentation conventions, variables are categorized into **core variables** (consistently populated across all records) and **additional variables** (context- or hierarchy-specific fields).

### 3.1 Unique Cross-Corpus Identifier
The unique primary key for every observation is **`cid`** (the official YouTube Comment Identifier, e.g., `UgzAtfjNJ-IOns7XAKh4AaABAg`). The `cid` guarantees unambiguous linkage between parent comments and child replies, as well as downstream merging with manual annotation files (`gold_standard.csv`) and machine classification outputs (`labels.csv`).

### 3.2 Core Variables

#### Table 2: Core Variables of the Comments Corpus
*Data on individual comment records ($N = 2,371$)*

| `variable` | Description |
| :--- | :--- |
| `cid` | The unique alphanumeric identifier assigned by YouTube to the comment. |
| `videoId` | The 11-character unique YouTube video identifier. |
| `videoTitle` | The full canonical title of the host YouTube video. |
| `pageUrl` | The direct URL to the source YouTube video. |
| `author` | The public handle/username of the commenting account (e.g. `@user-xyz`). |
| `comment_clean` | The cleaned, normalized text content of the comment (whitespace normalized, control characters stripped). |
| `comment_raw` | The verbatim raw text string as captured from the API payload (preserving original line breaks). |
| `publishedTimeText` | Relative publication timestamp at scrape time (e.g., `46 minutes ago`, `2 days ago`). |
| `voteCount` | Integer count of net upvotes (likes) received by the comment. |
| `replyCount` | Integer count of direct replies nested beneath the comment. |
| `type` | Comment hierarchy type indicator (`comment` for top-level root comments; `reply` for nested replies). |

### 3.3 Additional Variables
- **`replyToCid`**: Present only for nested replies (`type == 'reply'`). Contains the `cid` of the immediate parent comment to which the comment replies; empty string (`""`) for all top-level root comments.
- **`authorIsChannelOwner`**: Boolean flag (`True` / `False`) denoting whether the commenting user is the channel owner hosting the video.

---

## 4. Data Validation and Preprocessing Log

The integrity of `comments_clean.csv` was verified using the 5-step **ParlLawSpeech Data Validation Workflow** (`/datavalidation`). Documentation is a *claim* about the data; validation is what proves that claim true.

```
[Raw Apify Scrape: 2,385 rows]
        │
        ├─► Step 1: Structural Audit & CID Uniqueness Check (0 duplicate CIDs found)
        │
        ├─► Step 2: Source Integrity Check & Contamination Purge (-14 test rows removed)
        │           (Scraper default demo video 'xObhZ0Ga7EQ' identified and excised)
        │
        ├─► Step 3: Text Payloads & Encoding (0 empty texts, UTF-8 normalization)
        │
        └─► Result: [comments_clean.csv: 2,371 rows, 100% unique CIDs]
```

### 4.1 Cleaning Log and Audit Steps
1. **Header Normalization:** The raw export contained a UTF-8 BOM byte sequence and escaped quote delimiters in the first column (`\ufeff"author"`). These were cleaned into standard snakeCase/camelCase variable names.
2. **Identification and Removal of Contaminating Data:**
   - *Finding:* The raw scraper output contained 2,385 observations. During metadata inspection, exactly 14 rows were traced to `videoId == 'xObhZ0Ga7EQ'` (`https://www.youtube.com/watch?v=xObhZ0Ga7EQ`).
   - *Diagnosis:* This URL corresponds to the default tutorial video provided by Apify ("Try YouTube Scraper for FREE"). It was inadvertently retained in the input queue during scraper configuration.
   - *Action:* The 14 contaminating promotional rows were completely purged, restoring 100% thematic fidelity to the three focal defense policy videos.
3. **Primary Key Uniqueness Verification:**
   - `cid` uniqueness check: $2,371$ distinct values out of $2,371$ rows. Zero duplicate keys.
4. **Text Payload Preservation:**
   - In accordance with reproducible data science standards, the exact raw string is preserved in `comment_raw`, while `comment_clean` standardizes whitespace, stripping tabulations and carriage returns to ensure robust CSV parsing across Unix and Windows environments.
   - Non-informative / duplicate texts: 37 instances of identical wording were detected (e.g. repeated short affirmations such as *"Slava Ukraini"* or bot-like slogans). In accordance with the PLS context-aware rule, genuine short repeats in public commentary are legitimately retained.

---

## 5. Data Access and Reproducibility

The finalized dataset, validation scripts, and subsequent classification tools are archived in a public, fully reproducible Git repository:
- **Repository:** `https://github.com/kockabalazs-arch/my-agent-skills`
- **Replication Directory Structure:**
  ```text
  ├── data/
  │   ├── raw/
  │   │   └── dataset_youtube-comments-scraper_2026-10-11_bibo_mb.csv
  │   └── processed/
  │       └── comments_clean.csv
  ├── scripts/
  │   └── validate_and_clean.py
  ├── docs/
  │   ├── codebook.md
  │   └── validation_stats.json
  └── README.md
  ```
- **License:** Open Access under the **Creative Commons Attribution 4.0 International (CC-BY 4.0)** license. Users are free to share and adapt the material provided appropriate credit is given.

---

## 6. References

- Schwalbach, J., Hetzer, L., Proksch, S.-O., Rauh, C., & Sebők, M. (2025). *ParlLawSpeech: A linked corpus of parliamentary speeches, legislative bills, and enacted laws*. Version 1.0. Available at: https://parllawspeech.org/
- Sebők, M. (2026). *Practical Social Research with Agentic Generative AI*. Manuscript / Course curriculum, Bibó István Szakkollégium.
- Sebők M., Ring O. & Máté Á. (2021). *Szövegbányászat és mesterséges intelligencia R-ben*. Budapest: Typotex. https://tankonyv.poltextlab.com
