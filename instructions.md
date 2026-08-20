# Defend your stack's carbon story

> **How you'll submit this lab**
>
> This repo is your lab. Fork it, do the work described below in your fork, then open a pull
> request back into this repository. An AI reviewer will check your PR against `rubric.md` and
> leave feedback directly on the PR. See `README.md` for the full workflow.

Complete **Green Software & Sustainable AI** before starting this lab.

This lab is **hands-on and presentation-shaped**: you will **build a short slide deck** that (1) **defends** your green-tech assessment with clear reasoning and honest limits, and (2) **proposes concrete improvements** mapped to the **four pillars** (carbon, energy, hardware, measurement) and, where useful, ideas from the **[Green Software Patterns](https://patterns.greensoftware.foundation/)** catalog.

You still choose **Path A** (forward-looking use case) or **Path B** (retrofit audit of something you already built). **Submit at least one path**; both paths end in the **same slide deliverable shape**. Doing both paths is welcome if you have time.

## Lesson alignment

- **Learning objectives:**
  - **Path A:** By the end, you can **apply** green-software thinking to a defined AI use case, **defend** your assessment in a stakeholder-style deck, and **propose** GSF-aligned solutions with traceable links to pillars and/or named patterns.
  - **Path B:** By the end, you can **audit** an existing bootcamp artifact, **defend** your findings in a deck, and **prioritize** improvements using the same GSF framing.
- **Uses concepts from today:** GSF pillars, honest framing (no greenwashing), **SCI-style thinking** (functional unit **R**, boundaries, what you would measure), and optional pattern references from the official catalog.

---

## Submission hygiene

- **Filenames:** Use clear, descriptive names (avoid vague names such as `deck1.pptx` or `final.pdf` with no context).
- **Scope:** Your **GitHub** repository must contain **only materials for this lab**—no unrelated projects, dumps, or personal files.
- **README:** In your GitHub repository, include a `README.md` that maps each committed file (for example exported `.pdf` / `.pptx` deck, images, notes).

**GitHub only:** Submit the URL to a **GitHub repository** that contains everything for this lab (Markdown, code, exports, images, decks). Do **not** submit a standalone Google Doc, Notion page, or cloud-only link as your primary deliverable—put sources or exports (for example `.md`, `.pdf`, `.pptx`, screenshots) **in the repository**.

## What you will submit

1. **Slide deck** committed to the repo as **`.pptx` / `.key` / `.pdf`** (your choice) — **8–14 slides** (not counting a title slide). Do **not** use a cloud-only deck link as the sole artifact.
2. **Optional but recommended:** Include your **lever table** (Path A) or **audit template** bullets (Path B) in the deck’s speaker notes or appendix **or** as a separate `.md` file in the repo.

Your deck must make it obvious **which path** you followed.

---

## Suggested slide flow (adapt, do not skip the intent)

Use this as a **story arc**; rename slides to match your voice.

| # | Intent | What belongs on the slide |
|---|--------|---------------------------|
| 1 | **Hook** | Use case or artifact in one line; why green software matters *here* (cost, risk, reputation — tie to lesson). |
| 2 | **“One unit of value”** | State **R** in one sentence (e.g. one resolved ticket, one generated report, one training run). |
| 3 | **Assessment defense — hotspots** | Where compute, data movement, or idle capacity **probably** concentrates; mark **repeated** work (caching candidates). |
| 4 | **Assessment defense — assumptions** | 3–5 honest guesses (region, model size, call pattern, retention). Say what you **do not** know yet. |
| 5 | **Pillars map** | Show how your hotspots touch **carbon / energy / hardware / measurement** (mini diagram or 2×2 is fine). |
| 6–9 | **Proposed solutions** | **At least four** improvements; each slide (or pair): **problem → change → which pillar(s)**; name a **[Green Software Pattern](https://patterns.greensoftware.foundation/)** only if it genuinely fits (do not force a match). |
| 10 | **Measurement plan** | What you would track for 1–2 weeks (tokens, calls per **R**, latency, cost as proxy, etc.) and what would count as success. |
| 11 | **Caveats** | No unverifiable “carbon neutral” claims; offsets vs SCI (lesson reminder); what you would validate next with the client or team. |
| 12 (optional) | **Before/after hypothesis** | “If we X, we expect Y% fewer duplicate model calls / lower E per **R**” — stretch from Path A table. |

**Tip:** Imagine a **skeptical stakeholder** on slide 3 or 4 — add one line: *“Why should we believe this?”* and answer with **evidence or explicit uncertainty** (measurement next step).

---

## Path A — Forward-looking green tech assessment

### Kick-off

1. **Pick a use case** (one only): either a **past bootcamp project/lab** or a **fictional but concrete** client scenario (one paragraph: who, what workflow, which model/API).
2. **First step:** Write one sentence: *“One unit of value for this system is: ___.”* — put this on slide 2 later.
3. **Expected output:** A clear, testable **R** you can defend in the deck.

### First 10-minute win (Path A)

Complete a **three-row table** (copy into speaker notes or a draft slide):

| Lever | Current assumption (honest guess) | Better alternative to explore |
| ----- | --------------------------------- | ------------------------------ |
| Model / size | | |
| Call pattern (batch, cache, sync) | | |
| Infra / region / retention | | |

**Then:** Sketch **slide titles only** (8–14) in a scratch list — you are planning the “defense + solutions” story before you polish visuals.

### CFU checkpoints (Path A) — Scaffolded steps → remove training wheels

**Recognize:** Read your use case and circle **repeated** operations (same prompt, same classification, same embedding).

**Apply:** Fill the table with **one** concrete change per row (even if approximate).

**Integrate:** Draft the **slide deck**:
- **Defense section:** hotspots + assumptions + stakeholder challenge (slides 3–5).
- **Solutions section:** ≥4 improvements, each tied to **≥1 GSF pillar**; optional pattern name + link from the catalog.
- **Close:** measurement plan + caveats (slides 10–11).

**Verify:** Use this checklist — tick all before you submit:
- [ ] I named **one** primary audience (e.g. COO, CTO) on slide 1 or 2.
- [ ] Every proposed solution maps to **at least one pillar** (label on slide or in notes).
- [ ] I avoided **unverifiable** claims (“carbon neutral”) unless I defined methodology.
- [ ] I linked recommendations to **business** outcomes (cost, latency, risk), not only “planet.”
- [ ] Deck is **8–14** content slides plus title.

**Stretch:** Add **before/after hypothesis** slide: “If we cache X, we expect Y% fewer duplicate model calls” and the metric you would watch for one week.

---

## Path B — Green retrofit audit (optional alternate)

Use this path if you prefer **“consultant reviewing legacy work”** instead of a forward-looking scenario. You can also treat it as **extra practice** after Path A.

### Kick-off (Path B)

1. **Select one artifact** from a **previous** lab or project (repo README, architecture note, notebook, or short demo script).
2. **First step:** Paste a **link or path** and write **50 words** describing what the system does — this becomes slide 1–2 material.
3. **Expected output:** A concrete reference another person could open.

### CFU checkpoints (Path B)

**Recognize:** Skim the artifact and mark **where compute probably concentrates** (API calls, training loop, large batch jobs).

**Apply:** Complete the **retrofit audit template** below (notes or appendix slide).

**Integrate:** Build the **same deck shape** as Path A: defend the audit (hotspots, assumptions, skeptic line), then **≥4 GSF-aligned solutions** (quick win / medium / strategic can be called out in slide titles or notes).

**Verify:** “Would a peer know what to do next from my slides?” + Path A checklist above (pillars, honesty, slide count).

**Stretch:** If logs/metrics exist, add **one** numeric proxy (e.g. calls per user session, average tokens per call) on the defense slides.

### Retrofit audit template

**Artifact:**  
**Primary user journey:**  
**Hotspots (compute / data movement):**  
**Green opportunities (prioritized):**  
1.  
2.  
3.  
**What I would measure to prove improvement:**  
**Risks / tradeoffs:**  

---

## Rubric (self or peer)

| | Needs work | Good | Strong |
|---|------------|------|--------|
| **Deck narrative** | Jumps around; no clear “defense then solutions” | Logical flow; audience clear | A skeptical reader could follow the argument slide by slide |
| **Defense of assessment** | Generic or ungrounded | Hotspots + assumptions + some uncertainty | Explicit **R**, honest limits, stakeholder “why believe this?” answered |
| **GSF-aligned solutions** | Vague tips, no pillar link | ≥4 changes with pillar labels | Patterns cited where relevant; measurement ties to **R** |
| **Honesty** | Overclaims | Caveats present | Uncertainty named; next steps to validate |

## Hint ladder

- **Hint 1:** Start from **repeated** work (Path A) or **obvious hotspots** (Path B) — usually the cheapest wins for your **defense** slides.
- **Hint 2:** For each solution slide, use a tiny footer: **Pillar:** … so you never orphan a recommendation.
- **Hint 3:** Pair **smaller model** with a **quality check** (sample eval), not blind downgrades — say that on the slide.
- **Hint 4:** Borrow **measurement** vocabulary from the lesson (SCI, **R**, boundaries, grid intensity) in one slide; keep it accurate, not buzzwordy.
