# Design — `wok-audit` Skill

**Date:** 2026-05-06
**Author:** Alan Vazquez, CFA — AI Lead, Kaxanuk
**Status:** Approved (brainstorming complete)
**Source framework:** [WOK Audit Framework](https://github.com/dan-the-quant/ETP/blob/main/WOK_Audit_Framework.md) — Dan the Quant
**Sibling skill:** `Investment_Strategy/.agents/skills/roast-me/`

---

## 1. Purpose

Translate the WOK (Ways of Knowing) Audit Framework into a Socratic coaching skill for the KN Hack Research Challenge 2026 repo. Stress-test an investment thesis through eight epistemological lenses — Reason, Sense Perception, Language, Memory, Imagination, Emotion, Intuition, Faith — and emit a scored audit the user can paste into `docs/context/memory.md` or share with the team lead.

The skill is a sibling to `roast-me`. Both are coaching counterparties. They differ in lens:

| Skill | Lens | Probes |
|---|---|---|
| `roast-me` | Quant mechanics | Lookahead, survivorship, leakage, costs, overfitting, capacity, reproducibility |
| `wok-audit` | Epistemology | By what means does the user *know* what they claim — across the eight WOKs |

Both coexist. Skill description must explicitly direct the user to `roast-me` if they want pipeline/guardrail review, and to `wok-audit` if they want epistemic audit of the *claims*.

## 2. Audience and voice

CFA-holders, quants, engineers building on the KaxaNuk framework. Voice is precise, technical, decisive. No hype. No investment advice. Coach, not gatekeeper.

## 3. Trigger surface

Skill description fires on phrases such as:

- "audit my thesis", "WOK audit", "epistemic check"
- "is my thinking sound", "by what means do I know this"
- "score my reasoning", "audit how I'm reasoning"
- "apply ways of knowing to my strategy"
- User locking a strategic decision and asking for an epistemic review before committing

It does **not** fire on requests for guardrail review, code review, backtest critique — those route to `roast-me`.

## 4. Inputs

**Thesis memo only.** A markdown / doc / pitch describing the strategy, signals, universe, rationale, and stated convictions. No code reading. No config inspection. No backtest re-running.

If the user pastes backtest numbers as part of the memo, they may be cited as evidence under WOK 2 (Sense Perception) or WOK 4 (Memory), but the skill does not probe pipelines or configs. That boundary is what keeps `wok-audit` distinct from `roast-me`.

## 5. The eight WOKs

Loaded verbatim from the source framework. Each WOK has a core question, a checklist, documented failure modes, and an AI-specific risk callout.

| # | WOK              | Core question |
|---|------------------|---------------|
| 1 | Reason           | Is the logic valid and internally consistent? |
| 2 | Sense Perception | What direct evidence grounds this? |
| 3 | Language         | Is the thesis stated precisely enough to be falsified? |
| 4 | Memory           | Does this account for historical precedent and regime context? |
| 5 | Imagination      | Are tail risks and non-historical scenarios considered? |
| 6 | Emotion          | Is sentiment or conviction treated as signal or noise? |
| 7 | Intuition        | Is expert pattern recognition acknowledged and examined? |
| 8 | Faith            | Is sustained conviction through disconfirmation defensible? |

## 6. Scoring rule

**Per WOK.** Two dimensions:

- **Deployment** ∈ {0, 1} — is the WOK actively present in the thesis?
- **Discipline** ∈ {-1, 0, +1} — if deployed, how rigorously? +1 truth-seeking and falsification-friendly · 0 present but unexamined · -1 misleading or confirmation-seeking.

**Score = Deployment × Discipline ∈ {-1, 0, +1}.**

**Aggregate = Σ(scores) / 8 ∈ [-1, +1].**

**Bands:**

- **+0.70 to +1.00** — exceptional epistemic diversity
- **+0.40 to +0.69** — solid; some WOKs underdeveloped
- **+0.10 to +0.39** — adequate but significant gaps
- **-0.10 to +0.09** — compromised; serious epistemological problems
- **below -0.10** — deeply problematic

**Evidence rule.** No score without a one-sentence user answer cited as evidence. The score is a conversation prompt, not a verdict. The user always sees what earned the score and can challenge it.

## 7. Session structure

Four phases. Don't announce the names — walk the user through.

### Phase 1 — Frame (1–2 turns)

Restate the thesis in one paragraph. Confirm with the user. Surface:

- The central claim — what is the user *claiming to know*?
- The falsifying condition — what would make them abandon it?
- The time horizon over which the thesis is supposed to play out.

Don't move on until the user agrees the framing is correct.

### Phase 2 — Triage (1 turn)

Agent proposes the 3–4 highest-leverage WOKs based on the thesis content. User confirms or swaps. Heuristics:

- Thesis built on backtest → Sense Perception, Memory, Reason
- Thesis built on personal intuition + small sample → Intuition, Faith, Imagination
- Thesis from an AI-generated screen or factor → Reason, Language, plus AI-Specific Risks across all eight
- Thesis built on conviction through prior drawdown → Faith, Emotion, Memory

The remaining WOKs still get a single L1 framing question in Phase 3 — they are *not* skipped, only light-touched.

### Phase 3 — Probe (the bulk of the session)

Deep-walk the 3–4 picked WOKs using L1/L2/L3 questions from `references/wok_question_bank.md`. Light-touch the others with one L1 question each.

Two to three questions per turn. Wait for the user. Score each WOK as evidence accumulates. If the user gives a thin answer, ask a sharper variant on the same lens before scoring.

### Phase 4 — Synthesize

Emit the scorecard (template in §8). Present inline. The user can paste it into `docs/context/memory.md` or hand it to the team lead.

## 8. Synthesis template

```
# WOK Audit — [Thesis Name] — [YYYY-MM-DD]

## Thesis (as I understood it)
[One paragraph, confirmed by user.]

## Scorecard
| WOK              | Deploy | Discipline | Score | Evidence (1 line) |
|------------------|:------:|:----------:|:-----:|-------------------|
| Reason           |  1/0   |   +1/0/-1  |  ±1   | [quoted answer]   |
| Sense Perception | ...    |   ...      | ...   | ...               |
| Language         | ...    |   ...      | ...   | ...               |
| Memory           | ...    |   ...      | ...   | ...               |
| Imagination      | ...    |   ...      | ...   | ...               |
| Emotion          | ...    |   ...      | ...   | ...               |
| Intuition        | ...    |   ...      | ...   | ...               |
| Faith            | ...    |   ...      | ...   | ...               |

**Aggregate:** [sum]/8 = [score]  →  Band: [exceptional / solid / adequate-with-gaps / compromised / deeply problematic]

## Top 3 lenses pulling the score down
1. **[WOK]** — [failure mode triggered, why it matters, the specific question the user could not answer cleanly].
2. ...
3. ...

## AI-specific risks present (if any)
- [Per WOK whose AI-Specific Risk applies — fluency-as-precision (Language), no episodic memory (Memory), no alarm system (Emotion), conviction without basis (Faith), etc.]

## Suggested next moves (prioritized)
1. [Concrete, checkable action that would raise the lowest WOK by one notch.]
2. ...

## What would change my mind on the scores
- [For each top low-scoring WOK, the specific evidence that would resolve it. This is the user's TODO list.]
```

## 9. Style rules

- **Coach, don't lecture.** Ask. State view only when the user is genuinely stuck or asks directly.
- **One thread at a time.** ≤3 questions per turn.
- **Steelman before scoring.** No -1 score on a WOK whose deployment was misread. Confirm the user's intent first.
- **No score without evidence.** Every cell in the scorecard cites a one-sentence user answer.
- **Specificity over abstraction.** "What does Reason claim that Memory does not check?" beats "is your reasoning sound?"
- **Mirror the user's terminology — but re-introduce the WOK label at scoring.** If the user says "I have conviction here", the agent scores Faith and Emotion explicitly so the user learns the framework as they go.
- **Flag, don't fix.** When you spot a Discipline=-1 trigger, name it and ask the user how they'd address it. They learn more, and they may have context the agent doesn't.
- **End every turn with one clear next step** — a question to answer or a check to run. No open-ended drift.
- **Philosophical lineage cited only on request.** The framework's lineage (Wittgenstein for Language, Bergson/Klein for Intuition, William James for Emotion/Faith, etc.) is operational scaffolding, not the deliverable. Reference only if the user asks.

## 10. When to stop

Stop probing and synthesize when any are true:

- The user has clean answers to every triaged WOK and the light-touch lenses have been covered.
- The user is repeating themselves on a question — push it into the synthesis with the score that already earned.
- The user signals fatigue or asks for the summary.
- New questions are no longer producing new information.

If the thesis is in genuinely good shape (aggregate ≥ +0.40), say so plainly in the synthesis. False low scores burn trust and make the next audit less useful.

## 11. File layout

```
Investment_Strategy/.agents/skills/wok-audit/
├── SKILL.md
└── references/
    └── wok_question_bank.md
```

### `SKILL.md`

YAML frontmatter (`name`, `description`, `metadata.version: 1.0`) + body covering: identity, boundary vs `roast-me`, audience, inputs, the eight WOKs, scoring rule, four phases, synthesis template, style rules, when-to-stop.

The `description` field is the trigger surface. It must be specific enough that the dispatcher fires `wok-audit` and not `roast-me` for epistemic queries, and explicit enough that the dispatcher fires `roast-me` and not `wok-audit` for guardrail queries. Include the disambiguation sentence: "If the user wants pipeline/code/guardrail review use `roast-me`; if they want an epistemic audit of the claims use `wok-audit`."

### `references/wok_question_bank.md`

Eight sections, one per WOK. Each section contains:

- **Core question** (verbatim from source framework).
- **L1 — Frame** questions (always covered, even for light-touch WOKs).
- **L2 — Probe** questions (covered for triaged WOKs).
- **L3 — Stress** questions (used when L2 is cleanly answered or the WOK is the heart of the thesis).
- **Failure modes** (verbatim from source framework).
- **AI-Specific Risk** (verbatim from source framework).
- **Discipline calibration**: what an answer worth +1 looks like, what a 0 looks like, what a -1 looks like — written as concrete one-line patterns so the agent can score consistently.

## 12. Out of scope (YAGNI)

- No code reading. No pipeline inspection. No config inspection. No backtest re-running.
- No multi-target polymorphism (target is thesis only).
- No long-form report deliverable (synthesis is the compact scorecard).
- No automatic invocation chaining with `roast-me` (sibling, not nested).
- No persistent score history across sessions. Each audit is self-contained.
- No automated writes to `docs/context/memory.md` — the user pastes the synthesis manually after reviewing.

## 13. Verification before "done"

Per `AGENTS.md` §3:

- `Investment_Strategy/.agents/skills/wok-audit/SKILL.md` exists, has valid YAML frontmatter, matches §11.
- `Investment_Strategy/.agents/skills/wok-audit/references/wok_question_bank.md` exists, covers all 8 WOKs with L1/L2/L3 + failure modes + AI risk + discipline calibration.
- The strategic decision (adopt WOK Audit Framework as a sibling skill to `roast-me`) is logged in `docs/context/memory.md` with today's date.
- No standing guardrail in `docs/context/lessons.md` is violated — currently the lessons file is empty, so this reduces to the standing guardrails noted in `AGENTS.md`.

## 14. Open questions

None. All Q1–Q6 brainstorm questions answered:

- Q1 → A (sibling to `roast-me`)
- Q2 → A (thesis only)
- Q3 → A (full scorecard with bands)
- Q4 → B (frame + triage 3–4 + light-touch rest)
- Q5 → A (thesis memo only as input)
- Q6 → A (compact scorecard as deliverable)
