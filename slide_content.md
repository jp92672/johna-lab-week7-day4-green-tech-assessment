# Feature Launch Kit: Green Audit Deck
## Path B — Green Retrofit Audit

---

### Slide 1: The Feature Launch Bottleneck Every Product Org Has

**Headline:** Features ship. Departments find out late.

- Siloed teams, delayed comms, no single source of truth
- Sales, CS, Marketing and every dependent team scrambling to catch up
- Weeks of road shows and enablement sessions just to align

**Bottom line:** Launch Kit automates enablement materials so every team is ready on day one.

**Audience:** Product Director and Engineering Lead evaluating org-wide rollout.

**[NOTES]**
Dependent departments means any team that needs to incorporate the release into their workflow: support scripts, sales decks, partner comms, dev docs, training, etc. The POC showed 3 doc types. At scale the kit covers whatever each channel needs. The audience for the kit output is each department directly: Sales to sell it, CS to support it, Marketing to generate pipeline, Dev to document it. Internal leadership are stakeholders in the system, not consumers of the kit.

---

### Slide 2: The RAG Journey to a Full Feature Launch Kit

**Headline:** From POC to org-wide enablement engine.

**POC today:**
- Static knowledge base, 3 fixed doc types, single feature scope

**At scale:**
- RAG over full product catalog, multiple file types as input
- Outputs expand: PPTs, PDFs, battle cards, dev docs, web content and more
- Triggered automatically when a feature ships

**One unit of value (R):** One completed launch kit per feature release.

**[NOTES]**
R is the functional unit from the SCI spec. Everything measured in this deck is expressed per R so improvements are comparable across release cycles and team sizes. The RAG upgrade path is explicitly documented by the original project team in rag_decision.md and project_structure.md.

---

### Slide 3: Where the Carbon Hides: Hotspots at Scale

**Headline:** Small POC, manageable cost. Scaled org, compounding problem.

- 3 LLM calls per kit, one per doc type, every feature release
- Full knowledge base injected into every prompt every time
- No caching: same kit regenerated each time a user requests it
- At 20+ features per year across a product org, every inefficiency multiplies

**Why believe this?** No telemetry exists yet. Cost and token count are the proxies. Measurement is step one.

**[NOTES]**
The skeptic question on this slide is answered directly: we are not claiming measured carbon data. We are reasoning from the architecture. The next step is instrumentation, not optimization.

---

### Slide 4: What We're Assuming (And Don't Know Yet)

**Headline:** Honest limits before the solutions.

**Assumptions:**
- Model: gpt-4o-mini used in POC ($0.15/M input, $0.60/M output). At scale, org selects model. Lighter alternatives (gpt-5 mini class) ran ~$0.125/M input but output costs vary.
- Call pattern: on-demand, no batching, no caching
- Region: default OpenAI inference region, grid intensity unknown
- KB size: small today, grows significantly at full product scale
- Retention: outputs not stored, so repeat requests re-run the model

**What we do not know yet:** tokens per kit, calls per release cycle, actual energy per R.

**[NOTES]**
Pricing figures from public OpenAI pricing pages, used as calculated estimates only. We do not have live token counts from the POC. The honest next step is instrumentation, not optimization. Model choice is an org decision; the POC default is not a prescription. Grid intensity matters because the same compute on a coal-heavy grid emits far more than on a renewable grid. We do not control OpenAI's inference region today. That is a real unknown and should be flagged to the client.

---

### Slide 5: GSF Pillars Map

**Headline:** All four pillars are in play.

| Hotspot | Carbon | Energy | Hardware | Measurement |
|---|---|---|---|---|
| Repeated LLM calls, no cache | X | X | | |
| Full KB in every prompt | | X | | |
| Single model for all doc types | X | X | | |
| No usage telemetry | | | | X |
| Idle infra between releases | | | X | |

**[NOTES]**
GSF pillars: Carbon efficiency (emit less per R), Energy efficiency (use less electricity per R), Hardware efficiency (use machines well, avoid idle capacity), Measurement (track real numbers, not assumptions).

Grounded in EU HLEG Trustworthy AI Guidelines, Requirement 6: Societal and Environmental Wellbeing. The Guidelines explicitly state that AI practitioners should prefer models with the lowest energy cost per successful task completion, considering architecture, hardware fit, and retry rate. Our pillars map operationalises that requirement for this specific system.

---

### Slide 6: Solution 1: Cache Kits Per Feature Release

**Problem:** Every user request re-runs the model even for the same feature.

**Change:** Store generated kits keyed by feature release ID. Serve from cache on repeat requests.

**Pillars:** Carbon, Energy

**Pattern:** Static Content (Green Software Patterns). Serve pre-generated output rather than regenerating dynamically.

**Expected impact:** Eliminates duplicate LLM calls per feature. Reduces API cost per release cycle with no quality tradeoff.

**[NOTES]**
This is the highest-leverage quick win. In a product org where multiple people request the same kit, caching cuts the majority of redundant calls with no quality tradeoff.

---

### Slide 7: Solution 2: RAG to Shrink Prompt Size

**Problem:** As the KB grows to cover the full product catalog, injecting it whole into every prompt becomes expensive and wasteful.

**Change:** Replace static injection with retrieval. Pull only the docs relevant to the current feature into the prompt.

**Pillars:** Energy, Carbon

**Expected impact:** Cost per kit stays flat as the product catalog grows. Token count per call does not scale with KB size.

**[NOTES]**
The team already documented this in rag_decision.md as the planned next step once the POC is validated. This solution is directly aligned with the team's own roadmap.

---

### Slide 8: Solution 3: Right-Size the Model Per Doc Type

**Problem:** gpt-4o-mini runs for all 3 doc types regardless of complexity.

**Change:** Route simpler outputs (customer FAQ, short email) to a lighter model. Reserve the larger model for complex outputs (sales battle card, solution brief).

**Pillars:** Carbon, Energy

**Caveat:** Pair with a quality check on sampled outputs before auto-distribution. Not a blind downgrade.

**Expected impact:** Lower inference cost per doc type. Faster generation on simpler outputs reduces latency and API spend.

**[NOTES]**
Model routing adds routing logic complexity. The quality check is non-negotiable: a lighter model that degrades output quality creates downstream rework costs that outweigh the energy savings.

---

### Slide 9: Solution 4: Batch Generation Over On-Demand Calls

**Problem:** Docs are generated individually on user request, creating fragmented and repeated inference sessions.

**Change:** Trigger full kit generation as a single batch job when a feature is marked ready. All doc types produced in one run.

**Pillars:** Hardware, Energy

**Expected impact:** Reduces idle inference time between calls. Kit is ready before any team has to request it, cutting time to enablement.

**[NOTES]**
Batch generation also aligns with the workflow naturally: the PMM marks a feature as ready to launch, and the kit is generated automatically at that trigger point rather than reactively on user request.

---

### Slide 10: Measurement Plan

**What to track for the first 2 weeks:**

- Tokens per kit (per R)
- LLM calls per feature release
- Cost per completed kit (cost as energy proxy)
- Cache hit rate once caching is implemented
- Latency per doc type (quality signal for model routing)

**What counts as success:** Cost per kit holds flat or decreases as feature volume scales.

**[NOTES]**
We are using cost as a proxy for energy because direct energy data from the OpenAI API is not available. This is an honest proxy, not a precise measurement. Document this assumption clearly with the client.

---

### Slide 11: Caveats & Honest Limits

- No live telemetry exists yet. Hotspot claims are reasoned estimates, not measured data.
- Carbon neutral is not claimed. SCI requires real grid intensity data we do not have.
- Offsets and RECs do not reduce SCI under the spec. Real reduction comes from the four solutions, not purchasing credits.
- Caching and batching add engineering complexity. Tradeoffs need scoping before committing.
- Model routing requires a quality validation step before going live.

**Next step:** Instrument the current POC for token and call counts before any optimization is applied.

**[NOTES]**
SCI is Software Carbon Intensity: carbon per one unit of useful work (R). The spec explicitly excludes market-based instruments from reducing the score. This is worth stating clearly to clients who expect offset purchases to satisfy sustainability goals.
