# VueConf Talk — Brainstorming Doc

**Status:** Active brainstorm  •  **Last updated:** May 5, 2026

---

## Talk Context

- **Speaker:** Will Marple
- **Conference:** VueConf
- **Slot:** Day 1, 10:00–10:40 AM (40 min)
- **Preceded by:** Evan You keynote, 9:00 AM — *"The Future of Vue and Tooling in an AI-Driven Frontend Ecosystem"*
- **Followed by:** Morning break (10:40)
- **Time until showtime:** ~2 weeks

> **Lucky positioning.** Evan sets the *thesis* (AI is reshaping the frontend/Vue ecosystem). Will delivers the *how*. Act 2 to Evan's Act 1.

---

## Talk Premise

**Title (LOCKED):** Stop Using One AI Tool for Everything: A Multi-Tool Approach to Frontend Development

**Original abstract (LOCKED — what's printed):**
> Effective AI-assisted development isn't about finding the best tool. It's about building workflows that use the right tool at the right time. This session breaks down a frontend pipeline that leverages multiple AI capabilities across the development lifecycle: design extraction, implementation, semantic code navigation, and visual verification using tools like Gemini, Claude Code, and MCP servers including Figma MCP, Serena, and Playwright. You'll learn progressive disclosure techniques for managing context as tasks move between tools, and walk away with mental models for designing workflows that play to each tool's strengths.

**Abstract reality check:** Written 8–9 months ago. Original Gemini→Figma→Claude pipeline is **obsolete** with Opus 4.7's 1M context. Used as opening joke. The *spirit* (multi-tool, vendor-agnostic) still holds.

---

## Working Constraints

- **NDA on day-job code.** → Solved via the harness viewer demo vehicle.
- **2 weeks of prep.** Forces ruthless scope.
- **Will rushes ~25%** → practice ~50 min for ~38 min delivery.
- **No co-builder for the React→Vue docs port.** Will is solo. Compresses to 1–2 days of focused work, but discipline required.

---

## The Big Question (the common thread)

**Refined thesis:** *Agentic engineering isn't about how much code you can produce — it's about how much code you can responsibly own. The new bottleneck is comprehension, not generation. So engineer your own harness.*

**The shock-and-awe punchline:**

> If you're reading every line of AI-generated code, you're not scaling.
> If you're not reading any of it, you're shipping dark code.
> Both are debt. The harness is how you escape the dichotomy.

**THE KEY FRAMING (elevated this round):** *The spec is the comprehension contract.*
- Plan creates the spec (the human-readable artifact you understand)
- Implementation is generated against it
- Eval verifies the implementation against the spec — behaviorally (Playwright) and architecturally (review)
- If the spec is readable and the eval passes against it, you don't need to read every line to responsibly own it

**Plan and Validate are bookends of the same artifact.** The spec is what you comprehend; the code is what you verify. This is the answer to the dichotomy.

---

## Recurring Threads / Motifs

1. **"The art of [live audio / engineering] is the art of turning things down."** — Use 3x: opening (framing), context-management section, close.
2. **AI moves fast** — Bookend. Open with "this abstract is already obsolete." Close with "and that's why the meta-skill matters more than the tool."
3. **Harness engineering** — You don't wait for the perfect tool; you build the harness. Today.
4. **The spec is the comprehension contract** — recurring callback that ties Plan and Validate.

---

## The Mental Model: levers + loop

**The four levers (what you tune):**
- **Prompting** — the instruction
- **Context** — the working set loaded right now
- **Memory** — the persistent knowledge across sessions
- **Tools** — what the agent can actually do

**The feedback loop:**
- **Evaluation against the spec** — closes the system; this is the comprehension-debt firewall

**Brief mention:** **Orchestration** as the multi-agent generalization (2 slides, not a section).

```
                 ┌─────────────────────────────────┐
                 │   Evaluation (against spec)     │  ← feedback loop
                 │  the comprehension-debt firewall│
                 └────────────────┬────────────────┘
                                  │
   ┌──────────┬───────────────────┼───────────────────┬──────────┐
   ▼          ▼                   ▼                   ▼          ▼
Prompting  Context              Memory              Tools     (Orchestration*)
```

Vendor-agnostic. Tools change; levers don't.

---

## The Demo Vehicle (LOCKED — the harness viewer)

**Concept:** A Vue 3 app that visualizes a project's agentic harness. Point it at a project directory; it surfaces and renders all the harness files (CLAUDE.md, AGENTS.md, .cursor/rules, .claude/skills/, etc.) in a navigable, comprehensible way.

**Why this is the right pick:**
- **Recursive authenticity.** The harness viewer IS what the talk is selling. Will is using his Vue harness to build the tool that visualizes Vue harnesses. That's the strongest possible "I am not asking you to do anything I haven't done."
- **Vehicle = cargo.** Demo time does double duty — every minute of demo airtime shows both the harness AND the methodology.
- **Has life beyond the talk.** Useful to anyone in the agentic-dev community, regardless of framework. Stars/forks beyond VueConf.

**Scope discipline (non-negotiable):**
- MVP only before recording the demo. The viewer needs to *work*, not to be feature-complete.
- Hard cap: ~3 days for a working v0.
- The on-stage demo shows ONE feature being added to it — *that's* the demo. The viewer doesn't need to wow on its own; it needs to be good enough to add to.

**Architecture (recommendation, Will to validate):**
- Vue 3 SPA + File System Access API (Chromium-only is fine for a demo)
- No backend; everything client-side
- Avoid Tauri/Electron — too much surface for the timeline

**On the Vue-specificness:** The viewer happens to be in Vue because we're at VueConf. The harness it visualizes works for any framework's agentic dev. State this once on stage and move on.

### Two repos shipped alongside the talk

1. **`vue-agentic-harness`** — the marquee artifact. Reusable harness for any Vue 3 project.
   - Progressive-disclosure code conventions docs (React → Vue port)
   - `CLAUDE.md` / `AGENTS.md`
   - Custom skills (Playwright eval, architectural review)
   - Spec templates + spec-generation pipeline
   - QA pipeline configs
   - README that's the talk in repo form
2. **The harness viewer Vue app** — uses the harness above; visualizes harnesses generally.

**Naming candidates** (Will to pick or invent): `harness-lens`, `belay` (climbing term — the system that catches you when you fall), `tether`, `vue-harness-viewer`, `harness-atlas`. The descriptive one is fine if nothing punchier feels right.

### The on-stage demo (recorded, narrated live)

**Plan → Implement → Validate** on a single feature being added to the viewer. ~5–7 min.

**Demo task candidates** (TBD — pick one):
- Add full-text search across harness files
- Add a "related files" panel that surfaces files referenced from the current one
- Add a tag/category sidebar parsed from frontmatter
- Add a diff view comparing two harness versions
- Add export-to-markdown of the entire harness as a single document

Selection criteria: small enough to demo in 5–7 min, big enough to exercise spec + state + UI + verifiable behavior. The "related files" or "search" features are probably strongest.

---

## Working Outline (v4 — incorporating spec-as-eval-artifact)

Target: ~50 min practiced → ~38 min live.

### 1. Cold open — "The art of turning things down" (3–4 min)

- Joke: abstract written 8 months ago is obsolete. Welcome to AI.
- 30 sec on the original premise; why it's obsolete.
- Pivot: pace of change isn't the threat — *mistaking tools for skills* is.
- Pro audio metaphor: "the art of live audio is the art of turning things down. As engineers, our job hasn't changed — take chaos, make it intelligible. AI just turned the volume up."
- Tee-up: how to engineer your own mixing board.

### 2. The trap (3–4 min)

- Two failure modes: read everything (don't scale) / read nothing (dark code).
- Both are debt: **velocity debt** and **comprehension debt**.
- Thesis: agentic engineering = the discipline of escaping this dichotomy. The harness is the way out.

### 3. The mental model: levers + loop (5–6 min)

- Four levers: Prompting / Context / Memory / Tools
- The feedback loop: Evaluation
- Brief: Orchestration as multi-agent generalization
- Vendor-agnostic. Tools change; levers don't.

### 4. The harness in practice — Plan → Implement → Validate (15–18 min, the meat)

Vehicle: the harness viewer. Frame: "here's how *I* do it; the structure is the point, not the tools."

- **4a. PLAN — the spec is the comprehension contract** (~5 min)
  - The spec as a first-class artifact, not a throwaway
  - **Key frame: "the spec is what we will comprehend; the code is what we will verify"**
  - Show the spec template from the harness
  - Brief on multi-agent spec generation (one example, not exhaustive)
- **4b. IMPLEMENT — tool-of-the-day** (~4–5 min)
  - Demo the implement step on the viewer (recorded)
  - Why Will reaches for Claude Code here
  - Vendor-resilience callback ("any of these would work — that's the point")
- **4c. VALIDATE — eval against the spec (the comprehension firewall)** (~6–8 min)
  - **Slow down here. This is where the talk earns its thesis.**
  - **Frame: "Plan and Validate are bookends of the same artifact"**
  - Custom Playwright skill verifies *behavioral* spec compliance (recorded clip)
  - **Architectural review** verifies *structural* spec compliance — does this match the architectural intent? (deep-dive — the chosen QA element)
  - The point: when the spec is the comprehension artifact, you don't need to read every line of code. You verify the code matches the spec.

### 5. Progressive disclosure & context management (3–4 min)

- Callback to the audio metaphor: "turning things down"
- Use the harness viewer to SHOW the progressive disclosure architecture of the docs system (the viewer literally renders this — perfect)
- Practical techniques: clean handoffs between Plan/Implement/Validate, narrowing each agent's context window

### 6. Harness engineering — the close (3–5 min)

- Empowering: don't wait for the perfect tool; build the harness today
- "You can ask for the capability you need and have it the same day."
- Concrete story: a harness component built fast (probably from the harness build itself — meta and authentic, no NDA)
- Final landing: *the meta-skill is engineering your own harness. Tools come and go. The harness is yours.*
- Plug both repos. Optional Evan callback if appropriate.

---

## Brain Dump (raw material captured for reference)

- Original abstract premise: Gemini 1M / Figma JSON / Claude. **Obsolete.**
- New angle: vendor-agnostic resilience; multi-tool fluency as professional insurance
- Pencil.dev + ChatGPT-5.5; OpenCode as alternatives
- Will's actual stack: Claude Code primarily; Pencil.dev sometimes; custom Playwright skill
- Spec-driven flow: plan → implement → validate
- Spec-driven *pipeline for producing specs* (multi-agent)
- Multi-agent orchestration (mention, don't deep-dive)
- Custom Playwright skill as eval layer
- QA pipeline: architectural review (CHOSEN deep-dive)
- QA pipeline: mutation testing (mention, not deep-dive)
- Progressive disclosure for context management
- Four levers: Prompting / Context / Memory / Tools
- Eval as feedback loop, against the spec
- "Comprehension debt" vs technical debt
- **The spec is the comprehension contract** (elevated insight)
- **Plan and Validate are bookends** (elevated insight)
- Force multiplication via relieving the code review bottleneck
- Harness engineering — build your own
- Iterative harness capability building
- Pro audio friend: "art of turning things down"
- Joke: AI moves fast / abstract dated
- Existing React-targeted progressive-disclosure docs system → Vue port (solo)

---

## Cut List (with reason)

- Original Gemini → Figma JSON → markdown workflow as a real demo. **Obsolete.** Joke setup only.
- Deep dive on Pencil.dev. Tool sprawl risk. One namedrop max.
- Mutation testing as a deep-dive. **Architectural review chosen instead.** Mention mutation testing as "we also do X for Y."
- Showing every cool tool. Tooling-tour failure mode.
- Live coding the demo on stage. Pre-record. Eliminate demo gods.
- On-stage walk-through of porting React conventions to Vue. Do that work before; present the result.
- Tauri/Electron for the harness viewer. SPA + File System Access API instead. Time discipline.

---

## Open Decisions (talk-level — in scope for these sessions)

- [ ] **Pencil.dev + ChatGPT-5.5** — sharpen specific moment or cut to one-line mention
- [ ] **Reach out to Evan** ahead of time for callback opportunities?
- [ ] **Final wording** of the one-sentence walkaway / closing line
- [ ] **The closing harness-built-fast story** — pick one (likely from the build itself once that's underway)
- [ ] **Concrete language** for the opening sequence (joke beat, abstract-is-obsolete pivot, audio-quote bridge)
- [ ] **Concrete language** for the "two failure modes" trap setup
- [ ] **Concrete language** for each of the four levers (a tight 30-second framing each)
- [ ] **Slide aesthetic / format approach** (typography, code presentation, motif visuals)

## Deferred to other sessions

These are real decisions but they live in a different workstream. We park them here so we don't lose them.

### App planning session (separate)
- The harness viewer's MVP scope and main features
- The on-stage demo task (which feature to add in the Plan→Implement→Validate walkthrough)
- Repo names (harness + viewer)
- Viewer's technical architecture (SPA approach validated, but specifics TBD)

### Research briefs to create (later — not this session, not necessarily next)
- Deep research on harness viewer approaches / competitive landscape / existing tools that visualize agent configs
- Deep research on architectural review patterns in agentic eval (what others are doing)
- Possibly: framing language / talk craft for thesis-driven AI talks (how others have landed comprehension/responsibility arguments)

---

## Stories / Demos / Examples Inventory

- [x] The opening joke
- [x] The pro audio friend quote (consider getting his name for humanity)
- [x] The on-stage demo: feature add on the viewer via the harness — TBD which feature
- [ ] One specific architectural-review catch — needs to be a real moment when the agent flags something a human reviewer would have missed. Can come from the harness build itself (no NDA — Will's own work).
- [ ] A "harness component built in an afternoon" story for the close — likely from the build itself
- [ ] Optional: a sanitized "vendor down" or "capability gap" moment — generalized from real experience

**NDA-safe story patterns:**
- "On a recent project..." (no specifics)
- "A pattern I see across teams..." (generalized)
- Hypothetical examples clearly framed as such
- **Stories from the harness/viewer build itself** ← this is the richest source. Will will be *living* these stories during prep.

---

## Prep & Practice Notes

### Pacing math (Will rushes ~25%)

- Past: 50 min practiced → ~35 min live (60-min target)
- For 40-min slot: practice ~50 min → ~38 min live
- Slide target: 100–115
- Pre-recorded demos help — don't compress like narration

### Two-week timeline (revised — solo on docs port)

**Week 1**
- Days 1–2: Vue 3 SPA scaffold for the viewer + minimum harness (CLAUDE.md, AGENTS.md, basic conventions doc skeleton)
- Days 3–5: React→Vue docs port + custom skills (Playwright, architectural review) + spec template — all happening **while building the viewer**, dogfooding
- Day 6: Viewer at MVP. Decide demo task feature. Spec it.
- Day 7: Record the Plan→Implement→Validate demo for the chosen feature

**Week 2**
- Days 8–9: Slides for sections 1–3
- Days 10–11: Slides for sections 4–6 (most slide-heavy)
- Day 12: First full timed run-through
- Day 13: Revisions; second timed run-through; publish repos
- Day 14: Travel / arrive / soundcheck

### Risk register

- **Demo failure on stage** → pre-recorded clips, slides as fallback
- **Rushing past the thesis** → put comprehension-debt slide twice if needed; never skim
- **Tool namedrops landing as ads** → frame every tool as "here's the lever it pulls"
- **Going over** → mark 2–3 elastic sections to compress
- **Viewer scope bloat** → MVP only, hard-cap features at "good enough to add to"
- **Solo docs port slipping** → if it slows, ship a smaller v1 of the docs and supplement post-conference. The talk needs *enough* docs to be credible, not exhaustive coverage.