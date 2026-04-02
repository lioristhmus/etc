# UlamAI Agent-Architecture Alignment Assessment

## Frozen snapshot

- **Assessment timestamp:** 2026-04-02 16:09:06 UTC
- **Original comment URL:** https://x.com/prz_chojecki/status/2039612350622314990
- **Repository under review:** https://github.com/ulamai/ulamai
- **Repository package version:** `0.2.11`
- **README status section:** `v0.2.11`
- **Latest visible tag at assessment time:** `v0.2.11` (2026-03-27, commit `90b0a31`)
- **GitHub Releases page at assessment time:** no formal releases published

## Scope and method

This note evaluates whether the public description in the linked X post is consistent with the **repository as implemented**, not whether the author may have a broader off-repo workflow.

The comparison is anchored to:

1. the post text as supplied in the chat and corroborated by public snippets,
2. the repository README,
3. the package metadata,
4. the tag/release pages, and
5. implementation files related to the informal `tex` proving route.

## Executive summary

The post is **directionally consistent only for the repository's informal `tex`-proving pipeline**.

It becomes **overstated if read literally as a full general-purpose “open problems in mathematics” research harness**.

What the repository clearly does implement is a **bounded, stateful, multi-role orchestration pipeline** for informal theorem proving / formalization, especially around the `tex` route:

- a planner-like component,
- worker-style draft generation,
- judge / verifier / domain-check stages,
- persistent whiteboard / repo-memory state,
- and final composition into a `.tex` proof draft.

What the repository does **not** clearly implement, at least in the visible code and docs, is:

- a dedicated **literature research agent**,
- a dedicated **computational exploration / counterexample search agent**, or
- a general long-paper orchestration system that matches the post's broader framing.

## Assessment matrix

| Claim in the post | Verdict | Repository-grounded assessment |
|---|---|---|
| Multiple agents/roles collaborate on proof work | **Yes, in spirit** | The `tex` path exposes planner, worker, judge, verifier, and composition roles. |
| An orchestrator/planner decides the next move | **Yes** | The code includes `tex_action_plan` and an action policy centered on `plan`, `solve`, `compose`, `write_memory`, and `give_up`. |
| Worker agents draft candidate arguments | **Yes** | The code includes `tex_claim_draft` and worker-oriented prompts with `worker_id`. |
| A verifier/judge checks for errors and gaps | **Yes** | The code includes `tex_claim_judge`, `tex_claim_verifier`, `tex_claim_domain_check`, and `tex_judge`. |
| There is a shared working memory / common base | **Yes** | The prompt schema includes `whiteboard_note`, `repo_reads`, and `repo_writes`. |
| The system starts with a whole-theorem attempt before decomposition | **Yes** | The `tex_monolithic_attempt` prompt explicitly asks for a “deep whole-theorem attempt” before subclaims. |
| Several agents edit a shared `.tex` base throughout the workflow | **Partially** | The repo has a `.tex`-proving route and final `.tex` composition, but the implementation is more structured than “many agents editing one free-form file.” It uses claims, accepted-claim ledgers, whiteboard state, and resumable artifacts. |
| The system is a full open-problem research harness with literature review | **No clear evidence** | Retrieval is aimed at mathlib / local repos / premises, not literature search. |
| There is a separate computational exploration / counterexample engine | **No clear evidence** | The repo is centered on Lean proving/formalization and proof-state search, not a distinct computational experiment subsystem. |
| It is meant for long papers, with length managed by the harness | **Not supported** | The docs explicitly list “Full proof automation for large papers” as a non-goal for now. |

## What strongly matches the repository

### 1. A bounded proof orchestrator really exists

The implementation includes a `tex_action_plan` entry point and a prompt that frames the system as a **bounded proof-orchestration planner** for informal LaTeX theorem proofs. The allowed next-step actions are explicitly structured around:

- `plan`
- `solve`
- `compose`
- `write_memory`
- `give_up`

This is very close to the post's intuition that an orchestrator coordinates different proof phases, decides how to proceed, and eventually assembles the result.

### 2. Worker / judge / verifier / checker roles are real implementation concepts

The code contains separate methods for:

- `tex_claim_draft`
- `tex_claim_judge`
- `tex_claim_verifier`
- `tex_claim_domain_check`
- `tex_compose`
- `tex_judge`

That is not just marketing language in the README. It is a real role separation in the implementation.

### 3. Shared persistent memory is part of the design

The prompt schema for the `tex` orchestration path includes:

- `whiteboard_note`
- `repo_reads`
- `repo_writes`

This is materially consistent with the post's idea of a common base that gets iteratively improved and checked.

### 4. The current `tex` route explicitly prefers a whole-theorem first attempt

The repository's own `v0.2.11` status note says that informal natural-language `tex` proving now begins with one deep whole-theorem attempt and only falls back to planner/worker claim decomposition if that first attempt fails verification.

That is a strong match to the post's “endgame” intuition where a more unified proof blueprint matters.

## Where the post overreaches relative to the repository

### 1. “Deep Research on Literature” is not evidenced as a subsystem

The repository docs describe retrieval primarily in terms of:

- `mathlib`,
- local repos / local declarations,
- explicit `--premises` files,
- and embedding / simple retrievers.

That is useful retrieval, but it is **not the same thing as an implemented literature-research agent**.

### 2. “Codex agent for computational explorations” is not clearly implemented

The repository does contain search, benchmarks, replay, and theorem-proving infrastructure, but not a clearly separate engine whose main purpose is to run numerical experiments, hunt examples/counterexamples, or perform generic exploratory computation in the way the post describes.

### 3. “3–10 agents in parallel” is a looser description than what the code exposes

The repository does have:

- `--tex-worker-drafts`,
- `--tex-concurrency`,
- planner / worker model overrides,
- and resumable artifacts.

So the post is not inventing the multi-worker flavor from nothing.

However, the implementation reads more like a **bounded multi-role pipeline** than an open-ended swarm of independent agents.

### 4. The long-paper framing is not supported

The post says that longer papers rely more on the harness and discusses a practical coherence limit per model.

That may be a valid empirical observation, but it is **not established by this repository**. In fact, the pipeline document explicitly lists **full proof automation for large papers** as a non-goal for now.

## Most accurate one-paragraph restatement

If this repository were described strictly from the code and docs visible on 2026-04-03, a more accurate summary would be:

> UlamAI currently implements a bounded, stateful informal-`tex` proving pipeline with planner / worker / judge / verifier style roles, shared whiteboard and repo-memory state, optional multi-worker draft generation, and final composition into a proof draft. It is well described as a theorem-proving / formalization orchestration tool, but not as a fully general open-problem research harness with dedicated literature-search and computational-exploration agents.

## Bottom line

- **Defensible reading:** the post is a loose, high-level description of the repository's `tex` proving route and its multi-role orchestration style.
- **Indefensible reading:** the post is a literal statement of end-to-end capabilities already implemented in this repository for broad mathematical research workflows.

In other words:

**the post is partly aligned in architecture, but broader than the repository's demonstrated implementation.**

## Evidence anchors

### Repository metadata and version freeze

- Repo home: https://github.com/ulamai/ulamai
- Package metadata (`version = "0.2.11"`): https://github.com/ulamai/ulamai/blob/main/pyproject.toml
- Tags page (`v0.2.11`, dated 2026-03-27): https://github.com/ulamai/ulamai/tags
- Releases page (no formal releases published): https://github.com/ulamai/ulamai/releases

### README / top-level docs

- README on repo home (contains `Status (v0.2.11)`, `tex` route, worker/concurrency flags, model suggestions, and pipeline overview): https://github.com/ulamai/ulamai
- Pipeline note (`Non-Goals`, including large-paper automation): https://github.com/ulamai/ulamai/blob/main/docs/pipeline.md

### Implementation files most relevant to the assessment

- `ulam/formalize/llm.py`:
  - `tex_action_plan`
  - `tex_monolithic_attempt`
  - `tex_claim_draft`
  - `tex_claim_judge`
  - `tex_claim_verifier`
  - `tex_claim_domain_check`
  - `tex_compose`
  - `tex_judge`
  - whiteboard / repo-memory prompt schema
  - URL: https://github.com/ulamai/ulamai/blob/main/ulam/formalize/llm.py

## Source note about the post text

The original X URL is included above as the authoritative public locator.

At assessment time, direct HTML extraction from that X status URL was not reliable in the retrieval tool, so the wording under review was treated as the **user-supplied post text**, which was also consistent with public search snippets.
