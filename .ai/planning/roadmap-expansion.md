# Slide Roadmap — v2 (body-heavy, illustrative, live cross-vendor demo)

**Status:** Draft for review · **Last updated:** 2026-05-18 · **Supersedes:** v1
**Current deck:** 25 slides · **Target:** ~60 slides for ~38-min delivery with live demo

## What changed since v1

- **Body becomes the vast majority** of the talk (~22–25 min on the harness tour).
- **No source-code walks** of harness-visualizer — too much for an audience. Every body slide is either a *concept diagram* or a *conceptual code snippet* that illustrates what's going on, not the implementation.
- **Progressive-disclosure docs get center stage** — the auto-authored `backend/docs/conventions/` + `frontend/docs/conventions/` with `path:line` evidence is the highlight pattern.
- **Demo collapses** from 7 framing slides to a **live cross-vendor moment** at the end: spin up the app, drive a feature via Claude Code + playwright-skill, then switch to pi.dev (GPT-5.5) and drive a different feature with the *same* skill.
- **Close tightens** to 4–5 slides — recap, callbacks, repos, thanks.

---

## The shape we're aiming for

```
§1  Cold open                  7 slides       ~3 min     │
§2  Trap                       2 slides       ~2 min     │ Framing
§3  Thesis + harness reveal    2 slides       ~1 min     │ (~7–8 min)
§4  Mental model               1 slide        ~2 min     │

§5  Vehicle reveal             2 slides       ~1 min     │
§6  THE BODY — the tour       ~40 slides     ~22–24 min  │ Body (~25 min)

§7  Live demo (cross-vendor)   3 slides       ~5–7 min   │
§8  Close                      5 slides       ~3 min     │ End (~10 min)
                              ───────                    
                              ~60 slides total
```

---

## What stays unchanged (25 slides already built)

§1 Cold open · §2 Trap · §3 Thesis · §4 Mental model · §5 Vehicle reveal + tree · §6 prompting skip → context (AGENTS.md → spec-gen pipeline → Claude/pi vendor) → memory (RRL → searchable) → tools (inventory → playwright) → eval (two layers → risk taxonomy) → demo tee.

All of those slides hold. The roadmap below threads **new slides between them** plus a small group at the end.

---

## §5 — Vehicle visualization (+2 between current S14 and S15)

#### NEW S14a · "harness-visualizer in motion"
- **Type:** Screenshot slide (full-bleed). Capture the running app on its own repo.
- **What the audience sees:** The force-directed graph w/ layer-colored nodes, Issues tab pinned. One sentence below: "Built with the harness you're about to see."
- **Talk:** "I'll come back to this at the end. For now, just register that it exists, and that the rest of this talk is the tour through what it surfaces."

#### NEW S14b · "Four lenses, one source of truth"
- **Type:** Four thumbnails (Graph · Table · Issues · Agents). No source code — just labels and one-line descriptions.
- **Talk:** "Same data, four views. Today we're walking through the *data*, not the views. The views are the demo."

> *Rationale:* These two slides anchor the recursive-authenticity hook before we tour the levers. The audience never sees the source code of the visualizer — only the surfaces.

---

## §6 — THE BODY (the tour) — total ~40 slides

Current 12 → target 40. Each lever becomes a richer mini-section. Every slide is a graphic or concept-card — **no project source code on screen**.

---

### §6.A · Prompting (1 slide — unchanged)

- **S15** (existing): "First stop: Prompting — you're already good at this."

---

### §6.B · Context — the deepest section (~17 slides)

Reframe Context as three motifs: **anchor**, **progressive disclosure**, **portability**.

#### B1 — Concept setup (+1 before existing AGENTS.md slide)

**NEW S15b · "Context = the working set right now"**
- **Graphic:** A horizontal bar split into three zones — *always-loaded* (cascade) · *on-demand* (search/fetch) · *never*. Annotate which kinds of harness files live in each zone.
- **Talk:** "Context isn't 'everything the agent could know.' It's what loads *right now*. Engineering context = deciding what goes where."

#### B2 — Anchor: AGENTS.md (1 existing + 1 new)

- **S16** (existing): "02 · Context — the canonical anchor" (AGENTS.md as constitution)

**NEW S16a · "Inside AGENTS.md"**
- **Graphic:** A mock document outline showing the real section headings from this project's AGENTS.md — *What this project is · Stack · Repo layout · Harness layer taxonomy · Diagnostic codes · Security rules · Conventions · Quality gates · Spec workflow · Roadmap · Out of scope · Working agreement.* Each as a labeled card with a one-line description.
- **Talk:** "This is what's in mine. Stack, layout, the data model, the *non-negotiable* security rules, the spec workflow. Tool-agnostic — Claude, Cursor, pi all read this same file."

#### B3 — Progressive disclosure: the docs system (5 new slides — the highlight pattern)

This is what was missing in v1. The auto-authored convention docs is the section's centerpiece.

**NEW S16b · "When AGENTS.md isn't enough"**
- **Graphic:** Two stacked rows — top: "AGENTS.md (one file, repo-wide)" → bottom: "but the backend isn't the frontend isn't the shared layer." Each workspace gets its own conventions.
- **Talk:** "AGENTS.md is the constitution. But every workspace has its own grain — backend conventions, frontend conventions, shared. One file can't carry all of it without bloating."

**NEW S16c · "Progressive disclosure, made of files"**
- **Graphic:** A tree fragment:
  ```
  backend/docs/conventions/
    patterns/   — HOW we build (error handling, validation, ...)
    features/   — WHAT we ship (scanner, manifest emitter, ...)
  frontend/docs/conventions/
    patterns/   — HOW we build (stores, components, ...)
    features/   — WHAT we ship (graph view, agent panels, ...)
  ```
- **Talk:** "Each workspace gets its own conventions folder. Patterns are HOW you build. Features are WHAT you've shipped. Agents only load what's relevant to where they're working."

**NEW S16d · "Photo-accurate, not generic"**
- **Graphic:** Two columns. **Generic template** (the bad version): "Vue 3 components should use the composition API…" — italicized, grayed out.  **Path-line evidence** (the good version): a markdown snippet showing `error-handling.md` with real citations — e.g. `Pattern: All routes wrap handlers in safeAsync(). Evidence: backend/src/routes/scanner.ts:42, backend/src/routes/manifest.ts:18`.
- **Talk:** "These docs aren't generic 'best practices.' They cite real code. `path:line`. When the docs say a pattern exists, you can navigate to where it lives."

**NEW S16e · "The docs author themselves"**
- **Graphic:** A 3-phase strip: **discover** (workspaces classified) → **scaffold** (folders created) → **author** (LLM writes pattern + feature docs with evidence). Below, a label: "Re-run when the code changes. Idempotent."
- **Talk:** "The plugin reads the codebase and writes the conventions. When code changes, you re-run it. Symbol-level anchors and staleness bands — HIGH/MEDIUM/LOW — flag drift."

**NEW S16f · "Why this is the harness, not the docs"**
- **Graphic:** A handoff diagram — *human* writes AGENTS.md (rules) · *plugin* writes pattern docs (HOW) · *plugin* writes feature docs (WHAT) · *every agent* reads them in disclosure order: AGENTS.md → workspace conventions → specs. Each arrow labeled with what's added at that hop.
- **Talk:** "AGENTS.md says what the rules are. The pattern docs say how to honor them. The feature docs say what's already built. Every agent reads exactly what it needs for the work it's doing. That's progressive disclosure — and it's all files."

#### B4 — Progressive disclosure: the spec pipeline (3 existing + 1 new)

- **S17** (existing): "02 · Context — progressive disclosure" — multi-agent research → discovery → requirements → design → tasks
- **S18** (existing): "02 · Context — same pattern, two tools" — Claude plugin vs pi skill

**NEW S18a · "The spec is the comprehension contract"**
- **Graphic:** A single spec icon in the center. Three labeled arrows: *Plan creates →* · *Code generates against →* · *Eval verifies against ↰*. Caption: "You comprehend the spec. The code you verify."
- **Talk:** "This is the framing that does the most work in the talk. Plan creates the spec — the artifact you understand. Code is generated against it. Eval verifies the code matches it. You don't have to read every line to own the system. You have to comprehend the spec, and trust the verification."

#### B5 — Portability across vendors (+1)

**NEW S18b · "Per-agent context patterns"**
- **Graphic:** A 5-column matrix.
  | | Claude Code | Cursor | Codex | pi.dev | Continue |
  |---|---|---|---|---|---|
  | Pattern | cascade-implicit | mixed | cascade-explicit | skill-scoped | directory-of-rules |
  | Primary file | AGENTS.md | .cursorrules | AGENTS.md | settings.json | rules/*.md |
  | Scopes | global/project/local | project | global/project | project | project |
- **Talk:** "Every tool loads context differently. The harness has to know each one's pattern. That's what manifest.toml summarizes — and what the visualizer renders."

#### B6 — Multi-scope architecture (+2)

**NEW S18c · "Three scopes, one harness"**
- **Graphic:** Three concentric rings — *global* (read-only `~/.claude/`, `~/.pi/`) · *project* (read/write repo files) · *local* (`.harness/local/`, per-dev overrides). Each ring labeled with what lives there.
- **Talk:** "Some context belongs to you across every project — your global skills, your auth. Some belongs to the project. Some belongs to *just you on this machine*. The harness respects all three."

**NEW S18d · "The harness summarizes itself"**
- **Graphic:** A small TOML-flavored snippet (illustrative, not literal):
  ```toml
  [meta]
  generated_at = "2026-05-18T20:21:04Z"
  
  [agents.claude-code]
  pattern = "cascade-implicit"
  token_total = 47631
  artifacts = 12
  
  [agents.pi]
  pattern = "skill-scoped"
  token_total = 12440
  ```
  Caption: "`.harness/manifest.toml` — the harness as a single token-budgeted summary file."
- **Talk:** "Token budget per agent. Pattern per agent. One emit, every agent can read it. This is how cross-vendor stays sane."

---

### §6.C · Memory (~8 slides — current 2 + 6 new)

Reframe: three substrates · structure · search · accumulation.

**NEW S18e · "Memory in three substrates"**
- **Graphic:** Three cards.
  - `.review/` — what changed and why
  - `specs/` — what we agreed to
  - `state.json` — where we are in the workflow
- **Talk:** "Memory isn't one thing. Three substrates, three questions."

**NEW S18f · "The RRL artifact — schema"**
- **Graphic:** A frontmatter block (conceptual):
  ```yaml
  type: IMPLEMENTATION
  timestamp: 2026-05-18T17:06:33Z
  risk_level: MEDIUM
  commit_ready: false
  files_changed: 7
  decision_count: 3
  diff_hash: a3f9c124
  ```
- **Talk:** "Every meaningful turn writes one of these. Typed, timestamped, risk-classified."

- **S19** (existing): "03 · Memory — the audit trail" — the .review/ tree + artifact example

**NEW S19a · "Risk + decisions, captured"**
- **Graphic:** Two compact cards side-by-side. Left: a HIGH-risk segment callout (`AGENTS.md:180–185 — policy inversion flagged`). Right: a decision log entry (`DEC-014 [EXPLICIT] Generated docs may override AGENTS.md for per-workspace specifics`).
- **Talk:** "High-risk segments flagged where they live. Decisions logged with confidence — EXPLICIT means you told me, INFERRED means I assumed. Both auditable."

- **S20** (existing): "03 · Memory — searchable"

**NEW S20a · "Specs as queryable history"**
- **Graphic:** A SQLite-ish snippet showing the FTS5 idea:
  ```sql
  -- chunks: per-section content (spec_name, kind, heading, content)
  -- chunks_fts: FTS5 mirror, kept in sync by triggers
  SELECT spec_name FROM chunks_fts
   WHERE chunks_fts MATCH 'scope-aware AND scanner';
  ```
- **Talk:** "No vector store. No fine-tune. Just structured artifacts and full-text search. The agent queries it on demand."

**NEW S20b · "Why the agent doesn't lose the thread"**
- **Graphic:** Three timestamped artifacts on a horizontal timeline (`2026-05-12 spec` → `2026-05-15 implementation` → `2026-05-17 implementation`). Above them, an arrow labeled "the next agent pulls only what it needs from this chronology."
- **Talk:** "When a new session starts, the agent doesn't read everything. It searches by relevance. The project's history is recallable, not memorized."

---

### §6.D · Tools (~8 slides — current 2 + 6 new)

Reframe: inventory · the design pattern · cross-tool sharing · automation.

- **S21** (existing): "04 · Tools — what the agent can actually do" (inventory)
- **S22** (existing): "04 · Tools — a worked example" (playwright-skill)

**NEW S22a · "The pattern: compress, then expand"**
- **Graphic:** A small flow: *agent* → *skill (200-token summary)* → *cache (full state)*. With a return arrow labeled "query by name on demand."
- **Talk:** "Every custom skill I build follows this shape. The agent gets a short summary; the detail stays in a cache the agent retrieves only when it asks. That's how you build tools that don't blow the context window."

**NEW S22b · "Cross-tool skill sharing"**
- **Graphic:** Two skill folders side-by-side: `.claude/skills/playwright-skill/` and `.pi/skills/playwright-skill/`. An arrow between them labeled "the same `bin/` scripts, exposed to both runtimes."
- **Talk:** "Skills written once, exposed to two runtimes. The playwright-skill lives in `.claude/skills/`; pi reads it through its own skills surface. Same tool, two agents."

**NEW S22c · "claude-build — five agents, three waves"**
- **Graphic:** A 3-row wave diagram.
  ```
  Wave 0   contracts          1× implementer
  Wave 1   parallel build     3× implementers
  Wave 2   integration        1× implementer  +  architect-reviewer  +  test-writer
  ```
- **Talk:** "Five agents on the team. Wave 0 sets the type contracts — no collisions. Wave 1 builds in parallel. Wave 2 integrates and reviews. Five agents, one feature."

**NEW S22d · "Hooks — the automatic harness"**
- **Graphic:** A minimal settings.json-ish block:
  ```jsonc
  {
    "hooks": {
      "PostToolUse": [".claude/hooks/rapid-review.sh"],
      "Stop":        [".claude/hooks/rapid-review-mark.sh"]
    }
  }
  ```
  Caption: "Every turn → an artifact. Every stop → a marker. Automatic."
- **Talk:** "Hooks are how the harness writes its own audit trail. Every tool call generates a review entry. Every session-end marks a stop. I don't have to remember; the harness remembers for me."

---

### §6.E · Evaluation (~5 slides — current 2 + 3 new)

- **S23** (existing): "05 · Evaluation — the loop closes" (behavioral + structural)

**NEW S23a · "A real architect-reviewer flag"**
- **Graphic:** A compact `.review/` excerpt — pick one HIGH-risk decision from a recent IMPLEMENTATION artifact. Show the flag, the action required, and the resolution. Label: "From this week's work. Not hypothetical."
- **Talk:** "Here's what the reviewer flagged on Monday. Subtle: a docs system was demoting AGENTS.md from primary source of truth. Reviewer caught it. I confirmed it was intentional. Logged."

- **S24** (existing): "05 · Evaluation — read closely, where it matters" (risk taxonomy)

**NEW S24a · "What you actually read"**
- **Graphic:** A simple decision tree fed by the risk taxonomy. *Boilerplate → scan and sign. Logic → read, trust tests. Blast radius → read every line. Irreversible → read twice, re-read after agent runs.*
- **Talk:** "This is the discipline. The taxonomy isn't a chart on a slide. It's a workflow."

**NEW S24b · "The loop, complete"**
- **Graphic:** A closed-loop diagram: *Plan (spec) → Implement (code) → Verify against spec (behavioral + structural) → Audit trail (RRL) → next Plan.* The spec icon is highlighted at the top.
- **Talk:** "Every move feeds the next. The spec is the comprehension contract. The eval is the firewall. The RRL is the receipt. That's the loop."

---

## §7 — Live demo (cross-vendor) — 3 slides + ~5–7 min live

This is the punchline beat: the same harness, two vendors, side-by-side proof.

#### NEW S25a · "Now we drive it live"  *(replaces current S25 tee)*
- **Graphic:** Two stacked rows — top: "**Claude Code** + playwright-skill → drive feature A in the browser." bottom: "**pi.dev (GPT-5.5)** + playwright-skill → drive feature B in the browser." Center caption: "Same skill, two runtimes."
- **Talk:** "I'm going to spin up the app. First with Claude Code driving — using the playwright-skill to exercise one part of the visualizer. Then I'll switch to pi.dev, GPT-5.5, *same skill*, drive a different part. The harness travels."

#### LIVE moment 1 — Claude Code + Playwright
- *No slide.* Switch to the running app. Agent does its thing.
- Fallback: if anything wobbles, a screenshot slide of the expected outcome is ready in the deck.

#### NEW S25b · "Switching runtimes"  *(a transition card)*
- **Graphic:** Big label "now pi.dev — GPT-5.5." Below: a faint reminder of the skill location (`.pi/skills/playwright-skill/` ↔ shared `bin/`). One sentence: "Same skill. Different agent."
- **Talk:** "Same skill files. Different runtime. Different model. Watch."

#### LIVE moment 2 — pi.dev + Playwright
- *No slide.* Drive a different feature in the browser.

#### NEW S25c · "What you just saw"
- **Graphic:** A two-row recap: *(Claude Code · feature A · time-to-result)* and *(pi.dev · feature B · time-to-result)*. Caption: "Two vendors. One harness. Same skill."
- **Talk:** "Two different agents, one custom tool I wrote once. *That's* what vendor-portability buys you."

---

## §8 — Close — 5 slides (~3 min)

#### NEW S26 · "You didn't read every line."
- **Graphic:** Big quiet slide. One line top: "You didn't read every line." One line bottom: "You also didn't ship dark code." A small caption under both: "That's the dichotomy escape."
- **Talk:** Land it slow. This is the comprehension-debt firewall punchline.

#### NEW S27 · "The spec is the comprehension contract"  *(callback)*
- **Graphic:** Reuse the S18a graphic (or a tightened version).
- **Talk:** "This is the move. You comprehend the spec. The code, you verify. The audit trail is the receipt."

#### NEW S28 · "The art of turning things down"  *(audio quote callback)*
- **Graphic:** The same quote slide design, reused.
- **Talk:** "I told you at the start: the art is turning things down. The harness is how engineers turn things down. Less noise, more signal — at scale."

#### NEW S29 · "Build your harness today"
- **Graphic:** A simple takeaway card: *Don't wait for the perfect tool. Build the harness for the next feature, today.* Below, two repo cards with QR codes: `harness-visualizer` · `vue-agentic-harness`.
- **Talk:** "Don't wait. The capability you need is one skill file away. Both repos are public. Star them, fork them, send PRs — and tell me what your harness looks like."

#### NEW S30 · "Thank you / Q&A"
- **Graphic:** Speaker name · Black Airplane logo · email · handle. "Questions?"
- **Talk:** "Thank you. I'll be at the break — find me."

---

## Total

| Section | Existing | New | Total |
|---|---:|---:|---:|
| §1 Cold open | 7 | — | 7 |
| §2 Trap | 2 | — | 2 |
| §3 Thesis + harness | 2 | — | 2 |
| §4 Mental model | 1 | — | 1 |
| §5 Vehicle | 2 | +2 | 4 |
| §6.A Prompting | 1 | — | 1 |
| §6.B Context | 3 | +13 | 16 |
| §6.C Memory | 2 | +5 | 7 |
| §6.D Tools | 2 | +5 | 7 |
| §6.E Evaluation | 2 | +3 | 5 |
| §7 Live demo | 1 | +2 | 3 |
| §8 Close | 0 | +5 | 5 |
| **Total** | **25** | **+35** | **60** |

---

## Recommended build order

1. **§6.B Progressive disclosure docs (S16b–S16f)** — the highlight pattern that was missing. Five slides. Highest priority.
2. **§5 Vehicle visualization (S14a/b)** — easy screenshot capture, lands recursive authenticity earlier.
3. **§8 Close (S26–S30)** — the deck has no ending right now.
4. **§7 Cross-vendor demo cards (S25a–c)** — small but high-stakes. Need the live moment to land.
5. **§6.B remaining context expansions (S15b, S16a, S18a–d)** — fills out the Context section to its 16-slide weight.
6. **§6.C/D/E expansions** — pick what excites you most; can be added incrementally.

---

## A few questions for you before we start building

1. **Cross-vendor demo features** — do you have two specific features in mind for the live moment (Claude Code feature A + pi.dev feature B)? Knowing the pair sharpens the recap slide (S25c).
2. **Pattern + feature docs** — do you have a `path:line`-cited example I should pull verbatim into S16d, or should I write a stylized one?
3. **Real architect-reviewer flag** — happy with the AGENTS.md-policy-inversion one from this week's RRL artifact for S23a, or do you have a better example in mind?
4. **Hooks slide (S22d)** — do you want the literal commands (`rapid-review.sh` paths) or a stylized version that reads cleaner on a slide?
