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

---

### 5. Imagination

**Core question:** Are tail risks and non-historical scenarios considered?

**L1 — Frame**
- Name a scenario that has *never* occurred in the historical sample but is plausible mechanically.
- What is the strategy's failure mode in that scenario — slow bleed, sudden crash, both?
- Is there a "this time is different" case the thesis is robust to?

**L2 — Probe**
- For each tail scenario you name, what is the mechanism — does it follow from a structural change, a correlation breakdown, a liquidity collapse, a policy shock?
- Are second- and third-order consequences considered? If your top names go to zero overnight, what does that do to the rest of the book?
- Are correlation-breakdown scenarios modeled, or are correlations assumed stable?
- Is tail risk being treated as synonymous with "historical worst case"? That is anchoring, not imagination.

**L3 — Stress**
- Construct an LTCM-style stress: simultaneous correlation regime shift across three asset classes you implicitly depend on. Does the strategy survive?
- For each scenario, write a falsifiable prediction: "if X occurs, the strategy loses Y." Now ask whether X is observable in real time.
- Are any of your "tail scenarios" actually plausible mechanically, or are they novel-sounding hallucinations? Each must be grounded in a historical analogue, a mechanism, *and* a falsifiable prediction.

**Failure modes:** Anchoring exclusively to historical distributions, treating tail risk as synonymous with historical worst-case, LTCM-style blindness to correlated failure modes, novel-sounding scenarios with no mechanism.

**AI-Specific Risk:** AI generates scenarios readily, but novel-sounding scenarios may be hallucinations. Every AI-generated scenario should be grounded in a historical analogue, a mechanism, and a falsifiable prediction. Ask: where is the analogue, the mechanism, the falsifier — for each scenario the AI proposed?

**Discipline calibration:**
- **+1** — non-historical scenarios named with mechanism and falsifier, second-order effects traced, correlation-breakdown modeled.
- **0** — scenarios listed but mechanisms vague; correlations assumed stable.
- **-1** — tail risk equated to historical worst case, AI-hallucinated scenarios with no mechanism, second-order effects ignored.

*Lineage:* Kant, Bachelard, Sartre.

---

### 6. Emotion

**Core question:** Is sentiment or conviction treated as signal or noise?

**L1 — Frame**
- Where does sentiment, positioning, or crowding enter the thesis — as input, as risk, or not at all?
- How is your *own* conviction in this thesis being examined for bias?
- Is there a rule for when sentiment becomes a buy or sell trigger?

**L2 — Probe**
- Is collective sentiment identified as a *variable* (with a measurement and a threshold), or treated narratively?
- How would you distinguish a genuine contrarian signal from premature positioning that just looks contrarian?
- Have you addressed crowding risk? At a given AUM, how many other funds are in the same names with the same logic?
- Are there documented moments when *your* enthusiasm influenced a parameter choice or a hold-through-drawdown decision?

**L3 — Stress**
- If a crowding-collapse event hits the most consensus names tomorrow (Aug 2007 quant quake style), is your strategy on the right or wrong side of the unwind?
- Walk through your last three "high conviction" moments. What did you do, what was the outcome, and how would you re-score the conviction now?
- If you removed every emotionally-loaded word from the memo ("compelling", "powerful", "robust"), what is left? Is the thesis weaker or just less performed?

**Failure modes:** Dismissing sentiment data as "soft," ignoring crowding risk, mistaking enthusiasm for edge, holding through drawdown due to emotional attachment rather than thesis integrity.

**AI-Specific Risk:** AI has no emotional stake in the outcome — which sounds like an advantage until you realize it also has no alarm system. It will not feel that something is wrong. Ask: where in this thesis would a seasoned PM's gut tighten — and did the AI flag it?

**Discipline calibration:**
- **+1** — sentiment as a measurable variable, own-conviction examined, crowding risk addressed with threshold.
- **0** — sentiment acknowledged narratively; own-conviction unexamined.
- **-1** — sentiment dismissed as soft, enthusiasm doing the work of evidence, crowding risk invisible.

*Lineage:* William James, Damasio, Feldman Barrett.

---

### 7. Intuition

**Core question:** Is expert pattern recognition acknowledged and examined?

**L1 — Frame**
- Where does practitioner judgment or pattern recognition enter the thesis — universe selection, signal design, override rules?
- Is the intuition based on documented prior experience, or undifferentiated gut feel?
- Has the intuition been stress-tested against an explicit rule?

**L2 — Probe**
- For every intuitive call in the thesis, can you point to a prior case where the same pattern produced the same outcome? How many cases? What was the hit rate?
- Is the intuition a real pattern or a label you put on a hunch after the fact?
- Have past intuitive calls been logged with date, decision, outcome? If not, the feedback loop is broken.
- How is intuition distinguished from motivated reasoning — the wish dressed up as a pattern?

**L3 — Stress**
- Take the strongest intuitive override in the thesis. What is the explicit rule it bypasses, and why is the override more reliable than the rule on the historical evidence?
- If a junior analyst applied the same intuition without your experience, would they reach the same conclusion? If yes, it is a rule, not intuition. If no, what specifically are *you* perceiving?
- For your top three intuitive calls of the past year — score each as right, wrong, or uncertain in retrospect. Is the hit rate above the rule-based baseline?

**Failure modes:** Passing off unexamined bias as expert pattern recognition, dismissing intuition entirely, overconfident intuition with no feedback calibration, confusing pattern recognition with confirmation bias.

**AI-Specific Risk:** AI produces outputs that *feel* intuitive to the reader. That feeling is the reader's own intuition being triggered by the AI's fluency — it is not the AI having intuition. Ask: when the AI gave you a "this looks like" answer, did you mistake its pattern-match for your own gut?

**Discipline calibration:**
- **+1** — intuitions named, prior cases cited with hit rate, feedback loop intact, distinguished from bias.
- **0** — intuition used but not examined; no documented track record.
- **-1** — gut feel labeled as pattern recognition, no feedback loop, motivated reasoning dressed as intuition.

*Lineage:* Bergson, Klein, Gigerenzer.

---

### 8. Faith

**Core question:** Is sustained conviction through disconfirmation defensible?

**L1 — Frame**
- What is the falsification threshold — at what point does the thesis fail and you exit?
- If the strategy enters a 20% drawdown tomorrow, is the holding period justified by the thesis logic or by hope?
- Is your position size proportionate to the *epistemic quality* of the thesis (the aggregate WOK score), or to the comfort of the conviction?

**L2 — Probe**
- Distinguish: when does sustained conviction reflect thesis integrity, and when does it reflect sunk cost?
- Has the thesis been stress-tested against the *specific* historical conditions under which strategies of this type have failed?
- If you imagine the thesis is wrong — fully wrong — what is the earliest signal that would tell you, and is it observable in real time?
- What is the kill switch — drawdown trigger, regime indicator, rolling-Sharpe threshold — and is it pre-committed in writing?

**L3 — Stress**
- Walk through a hypothetical 18-month period in which every individual signal degrades by 30% but no single one breaks the kill switch. Are you still in the trade? Why or why not?
- Is the conviction ideologically loaded — value, momentum, low-vol as identity — beyond the empirical support?
- If a peer with no skin in the game scored this thesis at +0.30 (adequate-with-gaps), would you reduce sizing? If not, what does that tell you about how the conviction is being held?

**Failure modes:** Holding through legitimate disconfirmation, abandoning sound thesis at first drawdown, ideological attachment to a factor or framework beyond its empirical support, sunk-cost masquerading as conviction.

**AI-Specific Risk:** AI has no convictions. But it will enthusiastically reinforce yours if asked to defend a thesis — and will do so with equal fluency whether the thesis is right or wrong. Ask: if you ask the AI to *attack* the thesis with the same vigor, does the attack hold up?

**Discipline calibration:**
- **+1** — falsification threshold pre-committed, kill switch observable in real time, sizing proportionate to epistemic quality.
- **0** — thesis held conditionally but the conditions are vague.
- **-1** — sunk-cost conviction, ideological attachment beyond empirical support, sizing decoupled from epistemic quality.

*Lineage:* William James, Plantinga, Tillich.
