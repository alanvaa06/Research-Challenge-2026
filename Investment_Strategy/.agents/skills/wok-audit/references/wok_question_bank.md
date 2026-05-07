# WOK Question Bank

A reservoir of Socratic prompts for auditing an investment thesis through the eight Ways of Knowing. Pull selectively — don't fire questions verbatim or in bulk. Adapt to the user's terminology and to what they have already said. Two to three questions per turn is the ceiling.

Each section follows the same shape:

- **Core question** — the one-line lens at the heart of the WOK.
- **L1 — Frame** — always covered, even for light-touch WOKs. Confirms the lens is being deployed at all.
- **L2 — Probe** — standard pushback any reviewer would have. Cover for the 3–4 triaged WOKs.
- **L3 — Stress** — advanced or methodology-deep. Use when L2 is cleanly answered or the WOK is the heart of the thesis.
- **Failure modes** — patterns that trigger Discipline = -1.
- **AI-Specific Risk** — what to watch when the thesis or any of its inputs were generated or refined by an LLM.
- **Discipline calibration** — concrete one-line patterns for what +1, 0, and -1 look like, so the agent scores consistently.

Source framework: WOK Audit Framework (Dan the Quant). Philosophical lineage cited per WOK at the end of each section — operational, not pedagogical.

**Light-touch protocol:** When a WOK is not among the 3–4 triaged in Phase 2, pull **only the first L1 bullet** from its section. That single question confirms the lens is being deployed at all without burning a turn budget that belongs to the deep-walked WOKs.

---

### 1. Reason

**Core question:** Is the logic valid and internally consistent?

**L1 — Frame**
- State the thesis as a conditional: "If [premise], then [outcome], because [mechanism]." What are the three pieces?
- What are the explicit assumptions?
- Where does the conclusion come from — deduction from a model, inference from data, or both?

**L2 — Probe**
- Walk me from the premises to the conclusion in three to five logical steps. Where is the weakest link?
- Are any of the assumptions doing all the work? If you flipped the most fragile one, does the conclusion survive?
- Is anything in the chain confusing correlation with causation? What is the causal mechanism, in one sentence?
- If new data contradicted the conclusion, which assumption would you revise first?

**L3 — Stress**
- Translate the thesis into a formal model in your head. Are there internal contradictions between the model's parts?
- Is the reasoning circular — does the conclusion sneak into the premises (e.g., "this works because the backtest says it works")?
- If you removed every empirical input and reasoned from first principles, would the conclusion still hold? If not, what are you really claiming to know?

**Failure modes:** Circular reasoning, overfitting logic to a desired conclusion, treating model output as reality, mistaking correlation for causation, hidden assumptions doing the work.

**AI-Specific Risk:** AI reasons fluently within its training distribution with no awareness of when it has left it. High Reason scores in AI output do not imply the reasoning is grounded in current or relevant data. Ask: what would the model not know that a 2026 practitioner would?

**Discipline calibration:**
- **+1** — assumptions stated explicitly, chain is short and falsifiable, the user can name the one thing that would flip the conclusion.
- **0** — reasoning is present but unexamined; assumptions implicit; "it's logical" without showing the steps.
- **-1** — circular ("the backtest says so"), correlation-as-causation, or the conclusion appears in the premises.

*Lineage:* Aristotle, Descartes, Kant.

---

### 2. Sense Perception

**Core question:** What direct evidence grounds this?

**L1 — Frame**
- What is the *direct* empirical evidence supporting the thesis — prices, fundamentals, returns, volumes?
- What is the data source, and over what window?
- What does the data *not* see (private placements, dark prints, OTC)?

**L2 — Probe**
- Was the data point-in-time on every rebalance date — index membership, fundamentals, restatements?
- Have you actively sought *contrary* observations, or only confirming ones?
- Is the observation period representative of the regime you intend to deploy in, or only of the training window?
- For each metric you cite, name the source, the date, and the cleaning step. Where could a vendor revision break the result?

**L3 — Stress**
- If the data vendor reissued the dataset tomorrow and a value silently changed, would you notice? What is the audit trail?
- For micro-caps or thin lines, what fraction of your "observations" would actually be tradeable at the volumes the strategy implies?
- Distinguish: which claims are *empirical* (backed by direct data) versus *statistical* (derived from a model fit on data)? They are not interchangeable.

**Failure modes:** Cherry-picked samples, survivorship bias, conflating statistical fit with predictive validity, treating in-sample results as out-of-sample, point-in-time violations.

**AI-Specific Risk:** AI pattern-matches at scale and returns outputs that *feel* observational. They are statistical — derived from training data, not from direct market observation. Ask: did the AI cite a source, or did it summarize a pattern across an unspecified corpus?

**Discipline calibration:**
- **+1** — sources named, point-in-time honored, contrary observations sought, audit trail intact.
- **0** — data is cited but cleaning is opaque; vendor unspecified; window unjustified.
- **-1** — survivorship bias, in-sample posing as out-of-sample, cherry-picked window, or AI-summarized "facts" with no source.

*Lineage:* Locke, Hume, Russell.

---

### 3. Language

**Core question:** Is the thesis stated precisely enough to be falsified?

**L1 — Frame**
- State the thesis in one sentence with no hedge words.
- State the *falsification condition*: under what specific observation would you abandon it?
- Is the thesis stated as a claim with a prediction, or only as a description of how the world works?

**L2 — Probe**
- Define every load-bearing term — "value", "quality", "outperform" — what do they mean operationally? Pin each to a measurable.
- Could a sharp critic identify a specific prediction that, if wrong, overturns the thesis? Or are the predictions spongy enough to absorb any outcome?
- Where does the language perform certainty without substance — "we believe", "robust", "alpha-generative"? Translate each into a measurable claim.
- Distinguish in your own words: what is *known*, what is *assumed*, what is *speculated*. Are the hedges proportionate to the actual uncertainty?
- Has the thesis drifted since you wrote it down? If so, where, and was the drift logged?

**L3 — Stress**
- If you had to register the prediction in advance — date, magnitude, universe, falsifier — could you write it without resorting to "ish" and "approximately"?
- Is any key term doing double duty (carrying one meaning in setup, a different meaning in conclusion)?
- Pick the strongest falsifier you've named. Is it actually observable in your data, or is it phrased so it can never be triggered?

**Failure modes:** Vague hypotheses that cannot be tested, conflating description with prediction, language that performs certainty without substance, thesis drift, unfalsifiable hedging.

**AI-Specific Risk:** AI produces language with authority. Authority is not accuracy. This is the WOK where AI is simultaneously most capable and most dangerous — fluency creates the illusion of precision. Ask: if I deleted the adjectives, what is the testable claim that remains?

**Discipline calibration:**
- **+1** — falsifier named in measurable terms, every term defined operationally, claims and hedges proportionate.
- **0** — thesis stated but hedges unmoored; falsification condition vague.
- **-1** — unfalsifiable wording, "we believe" carrying load, terms drift between setup and conclusion, AI-fluent prose with no testable claim.

*Lineage:* Wittgenstein, Austin, Chomsky.

---

### 4. Memory

**Core question:** Does this account for historical precedent and regime context?

**L1 — Frame**
- What is the historical window the thesis stands on?
- Which market regimes does that window cover — rate cycles, volatility regimes, crisis episodes?
- What historical analogues are you implicitly betting are repeatable?

**L2 — Probe**
- Walk me through 2008 H2, 2011 Q3, 2018 Q4, 2020 Q1, 2022 calendar year. What was the thesis doing? What was the drawdown, and what was the exit rule?
- Are the analogues you cite genuinely analogous, or are you borrowing surface similarity (same direction, different mechanism)?
- Is the backtest period long enough to cover at least one full regime change? If not, what are you assuming about the next one?
- Does the work explicitly acknowledge what the historical record does *not* contain — sustained negative real rates, decade-long stagflation, regulatory regime changes?

**L3 — Stress**
- If the post-2010 low-rate, low-vol era is structurally over, which parts of the thesis still hold? Which collapse?
- Are there *structural breaks* in the data (post-Reg NMS, post-Decimalization, post-MiFID, post-COVID monetary regime) that the backtest blends across? If so, why is that valid?
- Pick the closest historical analogue and the closest historical *non*-analogue — the regime you'd lose money in. Why is the former more relevant than the latter to the next twelve months?

**Failure modes:** Overfitting to a single regime, recency bias, treating the last decade as representative of all time, ignoring structural breaks, false analogues.

**AI-Specific Risk:** AI has no episodic memory. It treats 2008 dynamics and 2024 dynamics with equal confidence and no sense of which regime the current moment resembles. Ask: when you used the AI for historical context, did it distinguish *which* regime it was reasoning from?

**Discipline calibration:**
- **+1** — multiple regimes covered, structural breaks named, the user can articulate which regime they are betting on next.
- **0** — backtest spans regimes but the user has not interrogated which regime the future resembles.
- **-1** — single-regime overfit, recency anchored, false analogues, structural breaks invisible.

*Lineage:* Bergson, Tulving.
