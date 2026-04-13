# COLLABORATOR FRAMEWORK
## Scientific Writing Collaborator — Q1 Strategic Layer

> **Purpose**: This is the *strategic* document. Read it at the start of every project. It defines the Q1 excellence pillars, guiding principles, story architecture, and the ethical AI collaboration protocol. It does not contain LaTeX rules, checklists, or grep commands — those live in `SUBMISSION_STANDARD.md`.
>
> **How to use**: Work through sections 0–3 before writing a single sentence. Fill in every bracketed placeholder. Run the AI prompts in §4 at least twice: once before drafting and once before submission. Update the changelog at the bottom after every submission and every round of reviewer feedback.

### Document Hierarchy

Three documents form the team's Q1 submission framework. Use them in this order:

| Document | Layer | When to Use |
|----------|-------|-------------|
| `MASTER_MANUSCRIPT_STANDARD.md` | Universal template | **Start here** for every new project. Contains project-agnostic rules, templates, and quality gates with bracketed placeholders. Copy and fill in for each manuscript. |
| `COLLABORATOR_FRAMEWORK.md` (this file) | Strategic layer | Complete before drafting. Defines scope, story, journal fit, and AI prompts. One per project. |
| `SUBMISSION_STANDARD.md` | Operational layer | Use during drafting and submission. Contains LaTeX rules, style rules, compilation sequences, and quality gate checklists. One per project. |

The `JCIM_REWRITE_V2026-04-11/GOLD_STANDARD_ROADMAP.md` is the project-specific instance from which both this document and `SUBMISSION_STANDARD.md` were derived. It remains as a reference for that specific manuscript.

* **Version**: 1.0 — April 2026
* **Companion document**: `SUBMISSION_STANDARD.md` (operational layer)
* **Status**: Living Document
* **Prepared by**: Nana Engo et al.


---

## CHANGELOG

| Date | Section | Change | Reason |
|------|---------|--------|--------|
| April 2026 | All | v1.0 created with a companion document: `SUBMISSION_STANDARD.md` (operational layer) | Strategic and operational content change at different rates; separation improves usability |

*Add a row after every submission and every round of reviewer feedback.*

---

## TABLE OF CONTENTS

0. [Q1 Excellence Framework](#0-q1-excellence-framework)
1. [Guiding Principles](#1-guiding-principles)
2. [Scope & Story Definition](#2-scope--story-definition)
3. [Journal Fit & Adaptation](#3-journal-fit--adaptation)
4. [Ethical AI Collaboration Protocol](#4-ethical-ai-collaboration-protocol)
5. [Red-Flag Dashboard](#5-red-flag-dashboard)
6. [Acceptance Probability Tracker](#6-acceptance-probability-tracker)

---

## 0. Q1 EXCELLENCE FRAMEWORK

Every manuscript submitted to a Q1 journal must be strong across all seven pillars before submission. A single weak pillar is sufficient grounds for desk rejection.

| Pillar | Q1 Criterion | Key Editorial Question | Verified by |
|--------|-------------|----------------------|-------------|
| **Novelty & Gap** | Clear, quantified advance vs. state-of-the-art | Why now? What is genuinely new rather than incremental? | §2.1 scope statement; Gate 10.10 in `SUBMISSION_STANDARD.md` |
| **Story Arc** | Obvious narrative spine readable in < 90 seconds | Can the entire story be summarized in one powerful sentence? | §2.2 story arc; AI prompt P2 in §4 |
| **Impact & Relevance** | Demonstrated practical or theoretical value with numbers | Why should a broad Q1 audience care? | §2.4 contribution statement; Gate 10.10 |
| **Visual Impact** | Figures understandable by a non-specialist in < 3 seconds | Do the graphical abstract and key figures sell the paper? | Figure rules in `SUBMISSION_STANDARD.md` §8; Gate 10.10 |
| **Reproducibility 2.0** | FAIR data + code + exact versions + convergence criteria + raw data | Can another group reproduce the work exactly? | Gate 10.10; `SUBMISSION_STANDARD.md` §6 |
| **Editorial Resilience** | Survives a 2-minute editorial scan (title + abstract + figures) | Desk-reject or send for peer review? | AI prompt P3 in §4; Gate 10.11 |
| **Reviewer Fit** | Methodological choices match the expert pool at the target journal | Will the assigned reviewers recognize and respect the approach? | §3 journal adaptation; Gate 10.9 |

**Golden Rule**: If any pillar is weak, the manuscript is not ready for Q1. Do not submit.

---

## 1. GUIDING PRINCIPLES

Ten non-negotiable principles that govern every manuscript from our research group.

| # | Principle | Enforcement |
|---|-----------|-------------|
| **P1** | **Honesty over ambition** — every claim must be supported by data actually present in the manuscript or supplementary information | Every sentence traceable to a table, figure, or calculation |
| **P2** | **Scope discipline** — the paper is exactly what the title says; no scope creep into tangential areas | Claims outside the stated scope are moved to "Future Work" or deleted |
| **P3** | **Transparent limitations** — state what the study cannot do before stating what it can | Dedicated limitations paragraph; honest caveats at every relevant point |
| **P4** | **No defensive writing** — results speak for themselves; justifications belong in rebuttal letters, not manuscripts | No sentence whose primary function is to pre-empt a reviewer objection |
| **P5** | **Zero AI-generated language** — no formulaic transitions, no hollow superlatives, no stock phrases | Full banned-pattern list in `SUBMISSION_STANDARD.md` §7 |
| **P6** | **Journal compliance by design** — every formatting requirement is satisfied structurally, not retroactively | Compliance checklist applied during writing, not after; see `SUBMISSION_STANDARD.md` §12 |
| **P7** | **No fabricated values** — all numerical results come exclusively from computed data; any value not backed by an actual calculation uses an explicit `[VERIFY]` placeholder | Placeholder audit during quality gates |
| **P8** | **Strategic citation depth** — the bibliography must be deployed to demonstrate scholarly command across multiple dimensions, not just method papers | Five-tier citation strategy in `SUBMISSION_STANDARD.md` §11 |
| **P9** | **Senior reviewer alignment** — the manuscript must satisfy both the technical reviewer (methodological rigor) and the editorial board (scope fit, novelty, impact, reproducibility) | Senior reviewer gate and editorial board gate in `SUBMISSION_STANDARD.md` §12 |
| **P10** | **Editorial resilience** — the manuscript must convince a Senior Editor in a 2-minute read of the title, abstract, and figures alone | AI simulation prompt P3 in §4 of this document; Gate 10.11 |

---

## 2. SCOPE & STORY DEFINITION

Complete this entire section before writing any part of the manuscript. These statements are the spine of the paper. If they cannot be written clearly, the science is not yet ready to be written up.

### 2.1 Single-Sentence Scope Statement (Q1 version)

Write exactly one sentence. No qualifications, no hedging.

**Template:**
> This work establishes **[specific advance]** by **[method/approach]** applied to **[dataset: size, diversity, type]** that **[quantified improvement or new insight]**, addressing a long-standing gap in **[subfield]** that has limited **[practical or theoretical consequence]**.

**Filled example (from our JCIM submission — replace entirely for your project):**
> This work establishes that GFN2-xTB and GFN1-xTB reproduce BP86/def2-SVP geometries for extended π-conjugated OPV molecules with sub-ångström hRMSD, sub-0.02 Å bond length MAD, and sub-1° angle MAD at 6–177× computational speedup, addressing a long-standing gap in efficient geometry generation for high-throughput OPV database screening that has limited the scale of next-generation ML training set production.

> ⚠️ **Replace the filled example above with your own project's statement. Do not leave the JCIM example in place.**

**Project-specific statement:**
> [WRITE YOUR SENTENCE HERE]

---

### 2.2 Story Arc

Write the full six-step arc before drafting. Each step is one to three sentences. This is not for the manuscript — it is a private navigation map.

**Step 1 — Broad Problem**
What real-world or scientific problem motivates this work? Why does it matter to a reader outside your subfield?
> [WRITE HERE]

**Step 2 — Specific Gap**
What is missing in the current literature that prevents the problem from being solved? Be precise: name the gap, not just the problem.
> [WRITE HERE]

**Step 3 — Method Used**
What approach, tool, or technique did you use to address the gap? One sentence. Do not mix in results.
> [WRITE HERE]

**Step 4 — Key Quantitative Finding**
What did you find, expressed in numbers? If you cannot write a number here, the paper is not ready to be written.
> [WRITE HERE]

**Step 5 — Transparent Limitations**
What can this work not do? What would falsify or weaken the claims? Name at least two.
> [WRITE HERE]

**Step 6 — Practical or Theoretical Impact**
What does this result enable? Use "enables" or "informs" — not "proves" or "demonstrates."
> [WRITE HERE]

---

### 2.3 What This Paper IS / IS NOT

| This paper IS | This paper IS NOT |
|--------------|------------------|
| [Precise description of what was done] | [Overclaim 1 — and why the data does not support it] |
| [Precise scope of datasets/systems] | [Overclaim 2 — and why this is a different research question] |
| [Precise scope of methods compared] | [Overclaim 3 — and why sample size or scope is insufficient] |

---

### 2.4 Honest Contribution Statement

Write exactly one paragraph of three to four sentences:

1. What was done (method and dataset — no results yet)
2. What the key quantitative finding is (one number minimum)
3. What the limitations are (at least one)
4. What this enables (not "proves" or "demonstrates")

> [WRITE YOUR PARAGRAPH HERE]

**Consistency check**: The contribution statement must be consistent with the title, the abstract, and the conclusions. If any of the three diverge from this statement, the scope has drifted — correct it before proceeding.

---

## 3. JOURNAL FIT & ADAPTATION

Select the target journal before drafting. If the paper cannot be placed in a specific cell of this table with confidence, the scope or framing needs revision first.

### 3.1 Target Journal

* **Primary target**: [JOURNAL NAME]
* **Fallback target**: [JOURNAL NAME]
* **Reason primary is appropriate**: [one sentence]
* **Reviewer Fit note**: [describe the likely expert pool and confirm the methodology matches their expectations]

### 3.2 Journal Adaptation Table

Expand this table as new journals are added to group workflows.

| Journal | Abstract limit | graphical abstract | Cover letter emphasis | Desk-reject risk | 2026 notes |
|---------|---------------|-------------|----------------------|-----------------|------------|
| JCIM | ~250 words | Required (square) | Methodology & benchmarking rigor | Medium | Perspectives section possible for broad benchmarks |
| JACS | ≤ 250 words | Required (square) | Broad chemical interest; strong motivation | Medium–High | Needs clear relevance beyond methodology |
| Angewandte Chemie | ≤ 150 words | Required | High impact, broad relevance | High | VIP and Communication formats differ |
| Nature Communications | ≤ 150 words | Required (landscape) | Cross-disciplinary relevance | Very High | Justify broad readership explicitly in cover letter |
| ACS Catalysis | ~250 words | Required | Mechanistic insight with catalytic relevance | Medium | Avoid pure methods papers without catalytic application |
| Chemical Science | ~250 words | Required | Originality and chemical insight | Medium–High | Gold open access; strong novelty bar |

### 3.3 Cover Letter Requirements

The cover letter must answer four questions explicitly, in this order:

1. **What is the advance?** One sentence stating the specific quantified finding.
2. **Why this journal?** One sentence on scope fit, not flattery.
3. **Why now?** One sentence on the gap this fills relative to recent literature.
4. **Who are the readers?** One sentence naming the audience beyond your immediate subfield.

> [DRAFT COVER LETTER OUTLINE HERE]

---

## 4. ETHICAL AI COLLABORATION PROTOCOL

The AI is never an author and never writes manuscript text. Its roles are strictly limited to:

- Pattern detection (banned language, inconsistencies)
- Technical compliance checking
- Story arc validation
- Senior Editor simulation
- Reviewer Fit assessment

### 4.1 Ethical Boundaries

| Permitted AI role | Prohibited AI role |
|------------------|--------------------|
| Flag banned patterns in submitted text | Write or rewrite any manuscript sentence |
| Identify logical gaps in the story arc | Generate results, numbers, or interpretations |
| Simulate editorial decision with justification | Appear in the author list or acknowledgements |
| Check consistency of numbers across sections | Suggest citations without human verification |
| Confirm formatting and structural compliance | Make scientific judgments about the data |

### 4.2 Ready-to-Use Prompt Library

Copy each prompt verbatim. Replace bracketed fields before use. Do not paraphrase — the precise wording matters.

---

**Prompt P1 — Zero AI-Pattern Check**

Use after every full draft of any section. Do not run on works-in-progress.

```
Analyze the following text and list ONLY the words or phrases that match
the banned patterns below. Do not suggest any rephrasing. Do not comment
on content, logic, or science. List each hit as: [word/phrase] → [category].

Banned categories and patterns:
- Hollow verbs: delve, underscore, illuminate, elucidate, showcase, harness,
  leverage (as verb)
- Hollow nouns: tapestry, testament, landscape, realm, paradigm, nexus,
  plethora, myriad
- Hollow adjectives: crucial, pivotal, paramount, indispensable, invaluable,
  unprecedented, groundbreaking
- AI transitions: Furthermore, Moreover, In addition, It is worth noting that,
  Notably, Importantly
- Self-congratulation: we demonstrate, we show, our work establishes,
  significantly improves
- Defensive framing: While it may seem that, Although one might argue
- Weasel words (when data is clear): suggests that, appears to, seems to indicate
- Redundant intensifiers: very, highly, extremely, remarkably, exceptionally
- Narrative clichés: In today's world, With the advent of, In recent years
- False humility: We acknowledge that, It is important to note that
- Vague scope openers: in this work (as sentence opener), state-of-the-art
  (used without quantification)

Text to analyze:
[PASTE TEXT HERE]
```

---

**Prompt P2 — Story Arc Validation**

Use at the end of a full draft, before the quality gates.

```
Read the following manuscript and perform two tasks.

Task 1: Summarize the single narrative spine a reader perceives in ONE clear
sentence of no more than 30 words. Do not describe what the paper does
section by section — identify the single through-line.

Task 2: Evaluate whether the story arc follows this structure:
(1) Broad problem → (2) Specific gap → (3) Method used → (4) Key quantitative
finding → (5) Honest limitations → (6) Practical impact.
For each step, state whether it is: Clear / Weak / Missing.
If weak or missing, state exactly what is absent — do not suggest replacement
text.

Manuscript:
[PASTE FULL MANUSCRIPT TEXT HERE]
```

---

**Prompt P3 — Q1 Senior Editor Simulation**

Use once before submission. Run for the primary target journal and, if time permits, the fallback journal.

```
You are the Senior Editor of [JOURNAL NAME, e.g. JCIM].
Your job is to decide in 60 seconds whether to desk-reject this manuscript
or send it for peer review.

Read ONLY the following: the title, the abstract, and the captions of
Figures 1 through [N], where N is the number of figures in the main text that carry the primary finding (typically 2-4). Do not read the full text.

Render your decision — desk-reject or send for peer review — and justify it
in exactly four bullets addressing:
1. Novelty: Is the advance clear and quantified?
2. Scope fit: Is this within [JOURNAL NAME]'s stated scope?
3. Visual impact: Do the figure captions suggest the figures are
   interpretable without reading the text?
4. Broad interest: Will a reader outside this subfield care?

Title: [PASTE TITLE]
Abstract: [PASTE ABSTRACT]
Figure 1 caption: [PASTE]
Figure 2 caption: [PASTE]
Figure 3 caption: [PASTE]
```

---

**Prompt P4 — Reviewer Fit Check**

Use when selecting between journals or after receiving a desk rejection.

```
You are a methodology expert in [SUBFIELD, e.g. computational chemistry /
machine learning for drug discovery].

Read the following methods section. Assess whether the methodological choices
(algorithms, datasets, statistical tests, comparison baselines) would be
recognized as appropriate and rigorous by a specialist reviewer at
[JOURNAL NAME].

List any methodological choices that a specialist reviewer might challenge,
and state exactly why. Do not suggest fixes — only identify the risks.

Methods section:
[PASTE METHODS SECTION HERE]
```

---

**Prompt P5 — Consistency Audit**

Use before the Consistency Gate (Gate 10.6 in `SUBMISSION_STANDARD.md`).

```
You will be given the abstract, results section, and conclusions of a
manuscript. Perform the following checks and report only failures:

1. Every number stated in the abstract also appears in the results section.
2. Every claim made in the abstract is supported by a result in the
   results section.
3. Every result mentioned in the results section is addressed in the
   conclusions.
4. The scope described in the abstract matches the scope described in
   the conclusions.

For each failure, state: [Location] → [Discrepancy].
Do not comment on writing quality or scientific merit.

Abstract: [PASTE]
Results section: [PASTE]
Conclusions: [PASTE]
```

---

### 4.3 Prompt Cadence

| Project phase | Run these prompts |
|--------------|-------------------|
| Before writing (scope & story) | P2 on the story arc outline in §2.2 |
| After each section draft | P1 (pattern check) |
| After full first draft | P1, P2, P5 |
| Before quality gates | P2, P3, P4, P5 |
| After revisions | P1, P3 |
| After reviewer feedback | P2, P4 |

---

## 5. RED-FLAG DASHBOARD

Run this check mentally before triggering the formal quality gates. If any flag is present, stop and fix it before proceeding to `SUBMISSION_STANDARD.md`.

| Red Flag | What it looks like | Fix |
|----------|--------------------|-----|
| Incremental novelty | The advance is a marginal parameter tweak with no new insight | Reframe around the insight, not the tweak; or change the target journal |
| No story arc | The paper reads as a methods report with no narrative tension | Return to §2.2 and write the arc explicitly before redrafting |
| Poor graphical abstract | The graphic requires reading the caption to understand it | Redesign with a non-specialist colleague as the test reader |
| AI-sounding language | Any item from the banned list (see `SUBMISSION_STANDARD.md` §7) | Run Prompt P1; revise flagged sentences |
| Missing limitations | Limitations appear only in the Discussion, buried after strengths | Add a dedicated limitations paragraph; move caveats to where the relevant result first appears |
| No reproducibility package | Code or data not publicly available with a DOI at time of submission | Deposit on Zenodo or GitHub before drafting the data availability statement |
| Scope mismatch | Title, abstract, and conclusions describe slightly different papers | Return to §2.1 and §2.3; align all three to the scope statement |
| Reviewer Fit gap | Methods are unconventional for the target journal's expert pool | Run Prompt P4; consider a methods paper as a precursor or a different journal |

---

## 6. ACCEPTANCE PROBABILITY TRACKER

This table is a heuristic based on group experience and empirical audit of our own submissions. It is not a guarantee. Numbers reflect manuscripts with solid underlying science; a fundamental methodological flaw is not recoverable through compliance alone.

Fill in the "Actual" column as you pass each milestone for the current submission.

| Milestone | Heuristic probability | Actual (this submission) |
|-----------|----------------------|--------------------------|
| Baseline — solid science, unpolished manuscript | 55–65% | |
| Story arc written and validated (§2.2 + Prompt P2) | 60–70% | |
| Quality Gates 10.1–10.8 passed (`SUBMISSION_STANDARD.md` §10) | 70–80% | |
| Senior Reviewer Gate passed (Gate 10.9) | 75–85% | |
| Editorial Board Gate passed (Gate 10.10) | 78–88% | |
| Q1 Editorial Simulation — "send for review" result (Gate 10.11) | **80–90%** | |

**Note on the numbers**: These ranges assume the science is sound and the novelty is genuine. The checklist and prompts improve the probability that solid science is communicated and packaged correctly. They cannot substitute for genuine methodological rigor, which is evaluated in Gate 10.9. These values are calibrated against our post-audit acceptance tracking (see `GOLD_STANDARD_ROADMAP.md` §21.11 for the JCIM benchmark case study).

---

*End of Collaborator Framework. Proceed to `SUBMISSION_STANDARD.md` for all operational rules, LaTeX specifications, quality gates, and pre-submission checklists.*
