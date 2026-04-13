# SUBMISSION STANDARD
## Scientific Writing Collaborator — Q1 Operational Layer

> **Purpose**: This is the *operational* document. Use it daily during drafting, revision, and final submission. It contains every LaTeX rule, style rule, quality gate, automated scan, and checklist needed to bring a manuscript to submission-ready state. It does not contain strategic guidance — that lives in `COLLABORATOR_FRAMEWORK.md`.
>
> **How to use**: Copy this file for each new project. Replace all `[BRACKETED PLACEHOLDERS]` with project-specific values. Apply quality gates in strict numerical order. Do not skip gates.

* **Version**: 1.0 — April 2026
* **Companion document**: `COLLABORATOR_FRAMEWORK.md` (strategic layer)
* **Status**: Living Document
* **Prepared by**: Nana Engo et al.

---

## CHANGELOG

| Date | Section | Change | Reason |
|------|---------|--------|--------|
| April 2026 | All | v1.0 created with companion document `COLLABORATOR_FRAMEWORK.md` (strategic layer) | Separation of strategic and operational content |


*Add a row after every submission and every round of reviewer feedback.*

---

## TABLE OF CONTENTS

1. [Document Architecture](#1-document-architecture)
2. [LaTeX Technical Specification](#2-latex-technical-specification)
3. [Journal Style Rules](#3-journal-style-rules)
4. [Anti-Fabrication & Reproducibility 2.0 Protocol](#4-anti-fabrication--reproducibility-20-protocol)
5. [Writing Style: Zero AI Patterns](#5-writing-style-zero-ai-patterns)
6. [Figure, Caption & Visual Language](#6-figure-caption--visual-language)
7. [Macro Consistency](#7-macro-consistency)
8. [Cross-Reference Rules](#8-cross-reference-rules)
9. [Bibliography Strategy](#9-bibliography-strategy)
10. [Quality Gates](#10-quality-gates)
11. [Pre-Submission Checklist](#11-pre-submission-checklist)
12. [Quick-Reference Card](#12-quick-reference-card)

---

## 1. DOCUMENT ARCHITECTURE

### 1.1 Standard Folder Structure

```
PROJECT_NAME/
├── MANUSCRIPT.tex                        ← Main document
├── MANUSCRIPT_SI.tex                     ← Supporting Information
├── BIBLIOGRAPHY.bib                      ← Single consolidated bibliography
├── COVER_LETTER.tex                      ← Cover letter
├── main_sections/
│   ├── 01_introduction.tex               ← Problem, gap, what this paper does
│   ├── 02_methods.tex                    ← Reproducible protocols, no results
│   ├── 03_results.tex                    ← Data presentation, no interpretation
│   ├── 04_discussion.tex                 ← Interpretation, context, limitations, guidance
│   └── 05_conclusions.tex               ← 3 paragraphs, synthesis only
├── SI_sections/
│   ├── S01_[METHOD_DETAIL].tex
│   ├── S02_[DATA_DETAIL].tex
│   ├── ...
│   └── SNN_[ADDITIONAL].tex
├── figures/                              ← All production figures
├── graphs/                              ← graphical abstract and supplementary graphics
└── response_to_reviewers/               ← Revision letters (created at revision stage)
```

### 1.2 Content Distribution Logic

| Content | Main | SI | Rationale |
|---------|:----:|:--:|-----------|
| Primary results | ✅ | | Core findings |
| Secondary results | ✅ (summary) | ✅ (full) | Space |
| Method details | ✅ (protocol only) | ✅ (theory, parameters) | Readability |
| Validation data | ✅ (key) | ✅ (complete) | Evidence |
| Statistical methodology | | ✅ (full) | Methods detail |
| Raw data tables | | ✅ (complete) | Space |

### 1.3 Section Purpose Rules

| Section | Must contain | Must not contain |
|---------|-------------|-----------------|
| **Introduction** | Problem, gap, scope, contribution | Results or numbers from the study |
| **Methods** | Exact protocols, software versions, convergence criteria | Results or interpretation |
| **Results** | Data presented neutrally; what was found | Interpretation, justification, argument ("this demonstrates", "this validates") |
| **Discussion** | Interpretation, comparison to prior work, limitations, practical guidance | Results tables repeated verbatim |
| **Conclusions** | Synthesis in exactly three paragraphs; no new information | Limitations, future work, tables, or figures |

---

## 2. LATEX TECHNICAL SPECIFICATION

### 2.1 Required Package Load Order

```latex
% 1. Document class
\documentclass[12pt]{article}  % or journal-specific class

% 2. Page layout
\usepackage[margin=1in]{geometry}
\usepackage{setspace}
\doublespacing

% 3. Mathematics (BEFORE font packages)
\usepackage{amsmath,amssymb}

% 4. Font (AFTER math packages)
\usepackage[T1]{fontenc}
\usepackage{newtxtext,newtxmath}

% 5. Units — siunitx v3 ONLY
\usepackage[detect-all=true,group-minimum-digits=4]{siunitx}

% 6. Tables
\usepackage{booktabs,longtable,tabularx,multirow}

% 7. Figures
\usepackage{graphicx,subcaption,float}

% 8. Color
\usepackage[table]{xcolor}

% 9. Bibliography
\usepackage[super,sort&compress]{natbib}

% 10. Hyperlinks (MUST be before cleveref)
\usepackage{hyperref}
\hypersetup{colorlinks=true, linkcolor=blue!60!black, citecolor=blue!60!black, urlcolor=blue!60!black}

% 11. External references (MUST be before cleveref)
\usepackage{xr}
\externaldocument[SI-]{MANUSCRIPT_SI}

% 12. Cross-references (MUST be last)
\usepackage[capitalise,nameinlink]{cleveref}
```

### 2.2 siunitx v3 Rules

| Construct | Correct (v3) | Incorrect |
|-----------|-------------|-----------|
| Value + unit | `\qty{0.018}{\angstrom}` | `$0.018$ \AA` or `0.018\,\AA` |
| Range | `\qtyrange{0.018}{0.021}{\angstrom}` | `0.018--0.021 \AA` |
| Uncertainty | `\qty{0.018 \pm 0.002}{\angstrom}` | `$0.018 \pm 0.002$ \AA` |
| Number only | `\num{29978}` | `29,978` or `29978` in prose |
| Unit only | `\unit{\angstrom}` | `\AA` |
| Scientific notation | `\num{1.0e-6}` | `$10^{-6}$` |
| Exponential notation | `\num{e4}` → **INVALID**; use `\num{10000}` | `\num{e4}`, `\num{e-3}` |
| Degrees | `\qty{0.72}{\degree}` | `$0.72^\circ$` |
| eV | `\qty{0.09}{\electronvolt}` | `$0.09$ eV` or `0.09\,eV` |
| Percent | `\qty{2.6}{\percent}` | `2.6\%` |

**Prohibited siunitx patterns:**
- `\SI{...}{...}` — v2 syntax; use `\qty{...}{...}`
- `\si{...}` — use `\unit{...}`
- Mixing math mode with siunitx: `$\qty{...}{...}$`
- `\num{eX}` patterns — siunitx cannot parse `e4`; write `\num{10000}`
- `S{}` column types in tables — they conflict with `\pm` and complex content; use `c` or `l` instead

### 2.3 Table Rules

- All tables use `booktabs` (`\toprule`, `\midrule`, `\bottomrule`)
- No vertical lines: no `|` in tabular preamble
- Captions **above** the table
- Sentence case for captions
- Units in column headers, not in every cell
- Sample sizes stated in caption or footnote
- Use standard column types (`l`, `c`, `r`) — never `S{}` columns with uncertainty notation

### 2.4 Compilation Order

Two sequences are defined. Use the **Development sequence** during drafting to speed up iteration. Switch to the **Final sequence** for the submission build.

**Development sequence** (faster; use during drafting):

```
1. pdflatex MANUSCRIPT_SI.tex
2. pdflatex MANUSCRIPT.tex          (reads SI .aux for xr)
3. bibtex MANUSCRIPT.tex
4. pdflatex MANUSCRIPT.tex
5. pdflatex MANUSCRIPT_SI.tex
6. pdflatex MANUSCRIPT.tex          (final pass)
```

Minimum three passes for main, two for SI. Cross-references are wrong until the final pass.

**Final sequence** (canonical; use for submission build only):

```
1. rm -f *.aux *.bbl *.blg *.log *.out *.toc *.lof *.lot   ← clean first
2. pdflatex MANUSCRIPT_SI.tex
3. pdflatex MANUSCRIPT.tex
4. bibtex MANUSCRIPT.tex
5. pdflatex MANUSCRIPT.tex
6. pdflatex MANUSCRIPT_SI.tex
7. bibtex MANUSCRIPT_SI.tex
8. pdflatex MANUSCRIPT_SI.tex
9. pdflatex MANUSCRIPT.tex                                  ← final
```

The clean step in the Final sequence is mandatory. Stale `.aux` files cause cross-reference errors that are invisible in development but fatal in production.

---

## 3. JOURNAL STYLE RULES

All text must conform to the target journal's style guide. The following rules are universally enforced and checked in Gate 10.3 (Style Gate).

### 3.1 American English

| Rule | Correct | Incorrect |
|------|---------|-----------|
| **-ize** endings | "optimization", "analyze" | "optimisation", "analyse" |
| **-or** endings | "behavior", "color" | "behaviour", "colour" |
| **-er** endings | "center", "meter" | "centre", "metre" |
| Single consonant | "modeling", "canceling" | "modelling", "cancelling" |
| "program" for software | "computer program" | "programme" |

### 3.2 Punctuation

| Rule | Correct | Incorrect |
|------|---------|-----------|
| Serial (Oxford) comma | "bonds, angles, and dihedrals" | "bonds, angles and dihedrals" |
| Periods inside quotation marks (US) | The term "benchmark." | The term "benchmark". |
| Em dash (no spaces) | "methods—particularly X—are" | "methods - particularly" or "methods--particularly" |
| En dash for ranges | `0.018--0.021` in LaTeX | `0.018-0.021` (hyphen) |
| Hyphens in compound modifiers | "high-throughput", "self-consistent" | "high throughput" |

### 3.3 Chemical and Technical Nomenclature

| Rule | Correct | Incorrect |
|------|---------|-----------|
| π-conjugated (Greek π, hyphenated) | "π-conjugated systems" | "pi-conjugated" |
| HOMO–LUMO (en dash) | "HOMO–LUMO gap" | "HOMO-LUMO gap" (hyphen) |
| Method names: preserve original casing | "GFN2-xTB", "BP86", "CREST" | "Gfn2-xtb", "bp86" |
| def2-SVP (lowercase def, hyphen) | "def2-SVP" | "Def2-SVP" |

### 3.4 Numerical Conventions

| Rule | Correct | Incorrect |
|------|---------|-----------|
| Numbers < 10 in prose | "three methods", "four datasets" | "3 methods" |
| Numbers ≥ 10 as numerals | "76 molecules" | "seventy-six molecules" |
| Numbers at sentence start | "Sixty-four molecules were..." | "64 molecules were..." |
| Decimal separator: period | "0.018 Å" | "0,018 Å" |
| Thousand separator: space or none | "29 978" or "29978" | "29,978" |
| Multiplication sign: × | "6× speedup" | "6x speedup" |

---

## 4. ANTI-FABRICATION & REPRODUCIBILITY 2.0 PROTOCOL

### 4.1 Numerical Value Categories

All numerical claims must fall into one of the following categories. No other category exists.

| Category | Allowed? | Requirement |
|----------|:--------:|-------------|
| Values from actual computations or experiments | ✅ | Must correspond to a table, figure, or calculation in the manuscript or SI |
| Values from cited literature | ✅ | Must have a verified citation with a complete bibliographic entry |
| Estimated or approximate values | ⚠️ | Must use `[VERIFY: describe what value is needed and from where]` |
| Fabricated values (invented for narrative flow) | ❌ | Never acceptable under any circumstances |

**Rule**: All `[VERIFY]` placeholders must be resolved before final submission. A placeholder audit is mandatory in Gate 10.7.

### 4.2 Reproducibility 2.0 Requirements

These requirements are mandatory for all Q1 target journals. They are verified in Gate 10.10.

- [ ] Public repository with a permanent DOI (Zenodo or GitHub with Zenodo archiving)
- [ ] All software versions listed explicitly (name, version number, and access date for online tools)
- [ ] All convergence criteria stated (tolerance values, iteration limits, grid settings)
- [ ] All input and output files deposited in the repository
- [ ] All analysis scripts deposited in the repository with a README
- [ ] FAIR compliance statement included in the Data Availability section of the manuscript:
  - **Findable**: data accessible via DOI
  - **Accessible**: data downloadable without login
  - **Interoperable**: data in an open format (CSV, JSON, XYZ, SDF, etc.)
  - **Reusable**: data carries an explicit license (CC BY 4.0 recommended)

---

## 5. WRITING STYLE: ZERO AI PATTERNS

### 5.1 Absolute Bans

Every item in this table is prohibited in the manuscript, SI, cover letter, and response to reviewers.

| Category | Banned patterns | Why |
|----------|----------------|-----|
| **Hollow verbs** | delve, underscore, illuminate, elucidate, showcase, harness, leverage (as verb) | AI filler; replace with precise verbs |
| **Hollow nouns** | tapestry, testament, landscape, realm, paradigm, nexus, plethora, myriad | Vague; replace with specific nouns |
| **Hollow adjectives** | crucial, pivotal, paramount, indispensable, invaluable, unprecedented, groundbreaking | Overclaiming; let data establish importance |
| **AI transitions** | Furthermore, Moreover, In addition, It is worth noting that, Notably, Importantly | Formulaic; use logical transitions instead |
| **Self-congratulation** | we demonstrate, we show, our work establishes, significantly improves | Argue results; do not announce them |
| **Defensive framing** | While it may seem that..., Although one might argue... | Belongs in the rebuttal letter, not the manuscript |
| **Weasel words** | suggests that, appears to, seems to indicate (when data is clear and direct) | State what the data shows |
| **Redundant intensifiers** | very, highly, extremely, remarkably, exceptionally | Unscientific; quantify instead |
| **Narrative clichés** | In today's world, With the advent of, In recent years | Stock phrases; start directly with the claim |
| **False humility** | We acknowledge that, It is important to note that | State limitations directly without preamble |
| **Vague scope openers** | In this work (as a sentence opener), state-of-the-art (without quantification) | Empty framing; name the specific advance |

### 5.2 Required Writing Patterns

| Instead of | Write |
|------------|-------|
| "X methods are highly accurate" | "X achieves a MAD of 0.018 Å against Y" |
| "This demonstrates the utility of X" | State the specific result |
| "Remarkably, X achieves..." | "X achieves [specific value]" |
| "We carefully established the protocol" | "Protocol: [specific steps listed]" |
| "The results suggest that X may be suitable" | "X achieves [specific metric] against Y on [dataset]" |
| "State-of-the-art methods" | "[Method name] (MAD = 0.018 Å)" |

### 5.3 Style Mantra

> **State the number. Name the method. State the comparison. Stop.**

---

## 6. FIGURE, CAPTION & VISUAL LANGUAGE

### 6.1 The 3-Second Rule

Every key figure must be interpretable by a non-specialist editor in less than three seconds. Test this by showing the figure (not the caption) to a colleague outside your subfield and asking them to state the main finding. If they cannot, redesign before submission.

### 6.2 Caption Rules

| Rule | Correct | Incorrect |
|------|---------|-----------|
| Sentence case | "Structural deviations of X from Y..." | "Structural Deviations of X from Y..." |
| Period at end | "...for the CEP dataset." | "...for the CEP dataset" |
| Sample sizes stated | "Sample sizes: n = 64 for A, n = 76 for B." | No sample sizes |
| Self-contained | Caption explains everything without reading main text | Caption refers to "results discussed above" |
| No interpretation in caption body | "Violin plots showing the distribution of deviations." | "Violin plots showing the excellent agreement." |
| Units stated | "Bond lengths in ångströms (Å)." | No units |
| Take-home message present | Italicized sentence at the end of the caption | Finding buried in the main text only |

### 6.3 Caption Template

```latex
\caption{Descriptive sentence-case caption ending with a period.
State what is plotted, the datasets shown, the comparison reference,
and sample sizes. Avoid interpretation or evaluation language in
the descriptive body.
Sample sizes: $n = [N_1]$ for [DATASET 1], $n = [N_2]$ for [DATASET 2].
\textit{Take-home message: [METHOD X] achieves a [METRIC] of [VALUE],
[outperforming / matching] [REFERENCE] by [DELTA].}}
\label{fig:label}
```

### 6.4 Graphical Abstract Requirements

- Landscape orientation preferred (check journal specs)
- Self-explanatory without reading the caption
- Main finding or advance visible in 3 seconds
- No text-heavy panels
- Sized to journal specification (check before creation, not after)
- File deposited in `graphs/` folder

---

## 7. MACRO CONSISTENCY

### 7.1 Defined Macros (single source of truth)

All macros defined in the preamble. No inline definitions scattered through sections. If a method or software name appears more than once in the manuscript, it must have a macro.

```latex
% Method/entity names — single definition, used everywhere
\newcommand{\methodA}{[METHOD A]\xspace}
\newcommand{\methodB}{[METHOD B]\xspace}
\newcommand{\software}{\texttt{[SOFTWARE NAME v0.0]}\xspace}

% Dataset names
\newcommand{\datasetA}{[DATASET A]\xspace}
\newcommand{\datasetB}{[DATASET B]\xspace}

% Math shorthand
\newcommand{\bm}[1]{\mathbf{#1}}

% Common metrics
\newcommand{\mad}{mean absolute deviation\xspace}
\newcommand{\MAD}{MAD\xspace}
```

### 7.2 Prohibited Patterns

| Pattern | Reason |
|---------|--------|
| Writing method names manually | Must use macro for consistency; one typo propagates everywhere |
| Writing software names manually | Must use macro; version number must be consistent |
| `\textcolor{blue/red/purple}{...}` | No revision marks in the submitted manuscript |
| Inline `\newcommand` inside section files | All macros defined in the preamble only |

---

## 8. CROSS-REFERENCE RULES

### 8.1 Main Document → Main Document

| Reference type | Command | Output |
|---------------|---------|--------|
| Section | `\cref{sec:intro}` | "section 1" |
| Figure | `\cref{fig:workflow}` | "figure 1" |
| Table | `\cref{tab:results}` | "table 1" |
| Equation | `\cref{eq:formula}` | "equation 1" |

**Rules:**
- Use `\cref{}` (lowercase) in running text
- Use `\Cref{}` (capitalized) at the start of a sentence
- Never use `\ref{}` or `\autoref{}`

### 8.2 Main Document → Supporting Information

```latex
% In main document preamble:
\usepackage{xr}
\externaldocument[SI-]{MANUSCRIPT_SI}

% Usage:
% \cref{SI-sec:method}    → "section S1"
% \cref{SI-fig:results}   → "figure S3"
% \cref{SI-tab:raw}       → "table S2"
```

### 8.3 SI Document Setup

Every SI document must include these counter redefinitions before any content:

```latex
\renewcommand{\thesection}{S\arabic{section}}
\renewcommand{\thesubsection}{S\arabic{section}.\arabic{subsection}}
\renewcommand{\thefigure}{S\arabic{figure}}
\renewcommand{\thetable}{S\arabic{table}}
\renewcommand{\theequation}{S\arabic{equation}}
```

**SI must have its own bibliography:**

```latex
\usepackage[super,sort&compress]{natbib}
...
\bibliographystyle{unsrtnat}
\bibliography{BIBLIOGRAPHY}
```

---

## 9. BIBLIOGRAPHY STRATEGY

### 9.1 Five-Tier Citation Deployment Map

Deploy citations across all five tiers to demonstrate scholarly command. A manuscript that draws only from Tiers 1 and 2 will be flagged by reviewers.

| Tier | Purpose | What to cite |
|------|---------|-------------|
| **Tier 1: Foundational methods** | Credibility anchor | Original papers for every method used or benchmarked |
| **Tier 2: Reference datasets** | Context anchor | Original publication for every dataset used |
| **Tier 3: Application domain** | Relevance anchor | Review papers and key application papers explaining why the work matters |
| **Tier 4: Alternative methods** | Fairness anchor | Papers describing at least three competing or complementary approaches |
| **Tier 5: Technical support** | Rigor anchor | Software papers, statistical method papers, basis set papers |

### 9.2 Citation Count Targets

| Metric | Target |
|--------|:------:|
| Citations in main document | 55–75 |
| Total bibliography entries | All relevant (no uncited padding) |
| Introduction | 25–35 |
| Methods | 10–15 |
| Results | 5–8 |
| Discussion | 10–15 |
| Conclusions | 2–4 |

### 9.3 Reviewer Red Flags

| Red flag | Fix |
|----------|-----|
| No citation to original method papers | Cite all Tier 1 papers |
| No citation to reference datasets | Cite all Tier 2 papers |
| No comparison to alternative methods | Cite at least three Tier 4 papers |
| Only self-citations or a narrow base | Deploy full breadth across all five tiers |
| Citations to preprints for key numerical claims | Replace with peer-reviewed sources where available |
| Bibliography entries with incomplete metadata | Audit all entries before Gate 10.8 |

---

## 10. QUALITY GATES

Gates must be passed in strict numerical order. Do not proceed to a later gate if an earlier gate has failures. Record the date each gate is passed.

| Gate | Name | Date passed |
|------|------|-------------|
| 10.1 | Compilation Gate | |
| 10.2 | Journal Compliance Gate | |
| 10.3 | Style Gate | |
| 10.4 | Technical Gate | |
| 10.5 | Content Gate | |
| 10.6 | Consistency Gate | |
| 10.7 | Placeholder Audit Gate | |
| 10.8 | Citation Deployment Gate | |
| 10.9 | Senior Reviewer Gate | |
| 10.10 | Editorial Board Gate | |
| 10.11 | Q1 Editorial Simulation Gate | |

---

### Gate 10.1 — Compilation Gate

- [ ] Main document compiles with zero errors
- [ ] SI document compiles with zero errors
- [ ] No LaTeX warnings in log file (cosmetic URL hyphenation warnings are acceptable)
- [ ] Bibliography resolves with no undefined citations
- [ ] All cross-references resolved (no `??` in the output PDF)

---

### Gate 10.2 — Journal Compliance Gate

- [ ] Title meets journal word limit
- [ ] Abstract meets journal word limit
- [ ] Keywords: within journal range
- [ ] Abbreviations: within journal limit (if applicable)
- [ ] graphical abstract present and correctly sized
- [ ] Author contribution statements present
- [ ] Data availability statement present with DOI
- [ ] Funding statement present
- [ ] Competing interests statement present
- [ ] Supporting Information is a separate compiled document

---

### Gate 10.3 — Style Gate

- [ ] American English spelling throughout (main + SI + cover letter)
- [ ] Serial comma used in all lists
- [ ] Sentence case for all headings and captions
- [ ] No banned words or patterns (§5.1)
- [ ] All numbers follow conventions (§3.4)
- [ ] Chemical and technical nomenclature correct (§3.3)
- [ ] Periods inside quotation marks (US style)
- [ ] Em dash used correctly (no spaced hyphens)

---

### Gate 10.4 — Technical Gate

- [ ] All `\qty{}` calls use siunitx v3 syntax
- [ ] All numbers ≥ 10 000 use `\num{}`
- [ ] No `\num{eX}` patterns anywhere
- [ ] No `S{}` table columns
- [ ] All cross-references use `\cref{}` or `\Cref{}` — no bare `\ref{}`
- [ ] All SI cross-references in main document use the `SI-` prefix
- [ ] All macros used consistently; no manual method or software names
- [ ] No `\textcolor{}` revision mark commands
- [ ] All tables use `booktabs` — no vertical rules
- [ ] All figure captions are self-contained, sentence case, end with a period, and include a take-home message line
- [ ] All tables have units in column headers and sample sizes in captions or footnotes
- [ ] Run the full automated scan (§11.2) with zero matches — confirms no manual Å, eV, degree, Hartree, 10^-X, or corrupted table headers

---

### Gate 10.5 — Content Gate

- [ ] No overclaiming beyond the scope defined in `COLLABORATOR_FRAMEWORK.md` §2
- [ ] Scope limitations explicitly acknowledged in the text
- [ ] No defensive writing in any section
- [ ] Primary results presented before secondary results in every subsection
- [ ] All interpretation confined to the Discussion section (not Results)
- [ ] Conclusions are three paragraphs, fit on one page, and contain no tables, figures, or new information
- [ ] A dedicated limitations paragraph is present in the Discussion

---

### Gate 10.6 — Consistency Gate

- [ ] Every number stated in the text matches a number in a table or figure
- [ ] Every claim made in the Introduction is delivered by a result in the Results section
- [ ] Every result mentioned in the Results section is addressed in the Discussion
- [ ] Every limitation stated in the Methods section is revisited in the Discussion
- [ ] Abbreviations defined on first use and used consistently thereafter
- [ ] The scope described in the abstract matches the scope in the conclusions
- [ ] Run Prompt P5 from `COLLABORATOR_FRAMEWORK.md` §4.2 and resolve all reported failures

---

### Gate 10.7 — Placeholder Audit Gate (Anti-Fabrication)

- [ ] Zero `[VERIFY]` placeholders remain anywhere in the manuscript or SI
- [ ] Every numerical value traces to a specific table, figure, or bibliography entry
- [ ] No value stated without a verifiable source

---

### Gate 10.8 — Citation Deployment Gate

- [ ] Target citation count (55–75) met in main document
- [ ] All Tier 1 foundational papers cited
- [ ] All Tier 2 reference dataset papers cited
- [ ] At least three Tier 3 application or review papers cited
- [ ] At least three Tier 4 alternative method papers cited
- [ ] At least three Tier 5 technical support papers cited
- [ ] No bibliography entry is uncited in the text (no padding)
- [ ] All bibliography entries have complete metadata (authors, journal, volume, pages or article number, year, DOI)

---

### Gate 10.9 — Senior Reviewer Gate (Methodological Rigor)

- [ ] All claims proportional to evidence actually presented
- [ ] Limitations of the reference method explicitly acknowledged
- [ ] Sample size limitations stated honestly
- [ ] All methodological asymmetries addressed (e.g., solvated vs. gas-phase comparisons, different optimization levels)
- [ ] Statistical methods reported with confidence intervals or equivalent uncertainty quantification
- [ ] Substructure or case analysis of failure modes included
- [ ] Practical guidance provided: when to use this method, and when NOT to use it
- [ ] Honest distinction between what is genuinely new and what confirms prior knowledge
- [ ] No defensive writing
- [ ] Run Prompt P4 from `COLLABORATOR_FRAMEWORK.md` §4.2 and resolve all identified reviewer risks

---

### Gate 10.10 — Editorial Board Gate (Scope, Impact, Reproducibility)

- [ ] **Scope fit:** Paper is unambiguously within the target journal's stated scope
- [ ] **Novelty statement:** A paragraph explicitly states what is new versus what confirms prior knowledge
- [ ] **Impact statement:** Practical or theoretical relevance established with concrete numbers
- [ ] **Reproducibility 2.0:** All §4.2 requirements met (public repository, DOI, versions, FAIR compliance)
- [ ] **Data availability:** DOI cited directly in the data availability statement
- [ ] **graphical abstract:** Present, correctly sized, 3-second rule satisfied
- [ ] **Author statements:** Contributions, funding, competing interests all present and complete
- [ ] **Reference quality:** All bibliography entries have complete metadata (Gate 10.8)
- [ ] **No scope creep:** Title, abstract, and conclusions describe identical scope

---

### Gate 10.11 — Q1 Editorial Simulation Gate (New)

Run Prompt P3 from `COLLABORATOR_FRAMEWORK.md` §4.2 for the primary target journal.

- [ ] Prompt P3 run for primary target journal
- [ ] Simulated decision is "send for peer review" (not "desk-reject")
- [ ] If the simulated decision is "desk-reject": identify the failing bullet, revise, and re-run before submission

**Note**: A "desk-reject" simulation result is not grounds to skip this gate — it is grounds to revise before submission. Record the simulation output and the changes made.

Simulated decision (record here): _______________
Date run: _______________
Changes made in response: _______________

---

## 11. PRE-SUBMISSION CHECKLIST

### 11.1 Final Compilation Sequence

Use the Final sequence (not the Development sequence) for all submission builds.

```bash
# Step 1: Clean all auxiliary files
rm -f *.aux *.bbl *.blg *.log *.out *.toc *.lof *.lot

# Steps 2–9: Full build
pdflatex MANUSCRIPT_SI.tex
pdflatex MANUSCRIPT.tex
bibtex MANUSCRIPT.tex
pdflatex MANUSCRIPT.tex
pdflatex MANUSCRIPT_SI.tex
bibtex MANUSCRIPT_SI.tex
pdflatex MANUSCRIPT_SI.tex
pdflatex MANUSCRIPT.tex          # final pass
```

Inspect the final `.log` files for errors before uploading.

### 11.2 Automated Scans

Run every scan and confirm zero matches before upload. A non-zero match count means the gate has failed.

```bash
# Banned AI patterns (extend this list as §5.1 is updated)
grep -riP '\b(delve|tapestry|testament|crucial|pivotal|paramount|indispensable|invaluable|unprecedented|groundbreaking|underscore|illuminate|elucidate|showcase|harness|nexus|plethora|myriad|Moreover,|Furthermore,|Notably,|Importantly,)\b' main_sections/ SI_sections/

# Self-congratulatory phrases
grep -riP '(we demonstrate|we show|our work establishes|significantly improves|it is worth noting|it is important to note)' main_sections/ SI_sections/

# Narrative clichés and vague openers
grep -riP '(In today.s world|With the advent of|In recent years|In this work,|state-of-the-art [a-z])' main_sections/ SI_sections/

# British English
grep -riP '\b(optimisation|parametrisation|behaviour|colour|centre|modelling|labelling|cancelling|programme)\b' main_sections/ SI_sections/

# VERIFY placeholders
grep -rn 'VERIFY' main_sections/ SI_sections/

# Manual Å (should be \unit{\angstrom} or \qty{}{\angstrom})
grep -rn '\\AA\b' main_sections/ SI_sections/

# Manual eV (should be \unit{\electronvolt} or \qty{}{\electronvolt})
grep -rn '\\,eV\|[0-9] eV\b' main_sections/ SI_sections/ | grep -v 'qty\|electronvolt'

# siunitx v2 syntax
grep -rn '\\SI{' main_sections/ SI_sections/
grep -rn '\\si{' main_sections/ SI_sections/

# Invalid siunitx exponential notation (causes compilation failure)
grep -rn '\\num{e[0-9]' main_sections/ SI_sections/

# Manual degree symbol (should be \qty{}{\degree})
grep -rn '\\circ\b' main_sections/ SI_sections/ | grep -v 'qty\|degree'

# Manual Hartree (should be \qty{}{\hartree})
grep -rn '\bHartree\b' main_sections/ SI_sections/ | grep -v 'qty\|hartree\|Coulomb'

# Manual 10^-X (should be \qty{}{} or \num{})
grep -rn '\$10\^' main_sections/ SI_sections/ | grep -v 'qty\|num'

# Bare \ref (should be \cref or \Cref)
grep -rn '\\ref{' main_sections/ SI_sections/ | grep -v 'cref\|autoref\|externaldocument'

# Revision mark colors
grep -rn '\\textcolor' main_sections/ SI_sections/
```

**Warning**: Automated text replacements (`sed`, find-and-replace) can silently corrupt LaTeX macros, especially table headers and macro names. Always verify table headers and all macro usages after bulk replacements. 
```

### 11.3 Final Metrics to Record

Complete this table and attach it to the submission record.

| Metric | Value | Target | Status |
|--------|:-----:|:------:|:------:|
| Main document pages | | 18–30 | |
| SI pages | | — (no limit) | |
| Title words | | ≤ journal limit | |
| Abstract words | | ≤ journal limit | |
| Keywords | | journal range | |
| Citations in main | | 55–75 | |
| `[VERIFY]` placeholders | | 0 | |
| AI language pattern hits | | 0 | |
| British English hits | | 0 | |
| Compilation errors | | 0 | |
| BibTeX warnings | | 0 | |
| Undefined references (`??`) | | 0 | |
| Multiply-defined labels | | 0 | |
| Simulation gate result | | Send for review | |

---

## 12. QUICK-REFERENCE CARD

### Do / Don't Summary

| Do | Don't |
|----|-------|
| Use `\qty{0.018}{\angstrom}` | Use `$0.018$ \AA` or `0.018\,\AA` |
| Use `\cref{fig:results}` | Use `\ref{fig:results}` or "Figure 1" |
| Use method and software macros | Write method or software names manually |
| State limitations honestly, before strengths | Hide limitations at the end of the Discussion |
| Use sentence case for all headings and captions | Use Title Case for headings |
| Use American English throughout | Use British English |
| Use serial comma | Omit serial comma |
| State the number, name the method, stop | Use "remarkably", "notably", "crucially" |
| Put all interpretation in Discussion | Put interpretation in Results |
| Use `[VERIFY]` for unverified values | Fabricate numbers for narrative flow |
| Cite Tier 1–5 papers strategically | Cite only self-references or only method papers |
| Pass all 11 quality gates in order | Submit after compilation check only |
| Use `\num{10000}` for large numbers | Use `\num{e4}` (invalid in siunitx) |
| Use standard `c`, `l`, `r` columns in tables | Use `S{}` columns with `\pm` values |
| Include a take-home message in every key caption | Leave the finding implicit in the figure |
| Deposit code and data with a DOI before submission | Submit without a public data repository |
| Run the Editorial Simulation before submitting | Skip Gate 10.11 because "the science is solid" |

### Quality Gate Sequence

```
Gate 10.1  Compilation Gate        → Does it build without errors?
Gate 10.2  Journal Compliance      → Does it meet every journal rule?
Gate 10.3  Style Gate              → American English, no banned patterns
Gate 10.4  Technical Gate          → siunitx v3, cleveref, macros, tables
Gate 10.5  Content Gate            → No overclaiming, honest limitations
Gate 10.6  Consistency Gate        → Numbers match, claims delivered
Gate 10.7  Placeholder Audit       → Zero [VERIFY] remaining
Gate 10.8  Citation Deployment     → 55–75 citations, all five tiers
Gate 10.9  Senior Reviewer Gate    → Methodological rigor
Gate 10.10 Editorial Board Gate    → Scope, impact, reproducibility, FAIR
Gate 10.11 Q1 Simulation Gate      → Simulated decision: send for review
```

---

*End of Submission Standard. This document is the operational companion to `COLLABORATOR_FRAMEWORK.md`. Apply both to every manuscript.*
