# Memory

> One-line entries. Format: `# decision: sentence`.

# stack: Python >=3.12,<3.15 + KaxaNuk Data Curator + KaxaNuk Backtest Engine.
# architecture: three sequential pipelines — Data Curator → Portfolio Construction → Backtest Engine (inferred from Investment_Strategy_Example/).
# entrypoints: run_data_curator.py, run_portfolio_construction.py, run_backtest_engine.py.
# config: Config/data_curator_parameters.xlsx, Config/backtest_engine_parameters.xlsx (inferred).
# custom-calc-modules: Investment_Strategy/src/data_curator/ registered in run_data_curator.py.
# testing: none found.
# governance: AGENTS.md (imported by CLAUDE.md) — Plan-before-act, Context/MEMORY.md + Context/SELF-CORRECTION.md required.
# wok-audit-skill: 2026-05-06 — adopted WOK Audit Framework as sibling Socratic-coach skill to roast-me; epistemic lens (Reason / Sense Perception / Language / Memory / Imagination / Emotion / Intuition / Faith); thesis-only input; scored Deployment×Discipline ∈ [-1,+1].
