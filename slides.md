---
theme: default
title: Stop Using One AI Tool for Everything
info: |
  ## Stop Using One AI Tool for Everything
  A Multi-Tool Approach to Frontend Development

  Will Marple — VueConf 2026
author: Will Marple
colorSchema: dark
highlighter: shiki
download: true
transition: slide-left
mdc: true
fonts:
  sans: 'DM Sans'
  serif: 'DM Sans'
  mono: 'JetBrains Mono'
  weights: '300,400,500,600,700'
  provider: google
drawings:
  persist: false
seoMeta:
  ogTitle: Stop Using One AI Tool for Everything
  ogDescription: A Multi-Tool Approach to Frontend Development — Will Marple at VueConf 2026
layout: cover
class: text-center
---

# Stop Using <span class="grad">One AI Tool</span><br/>for Everything

<div class="mt-6 text-2xl text-[color:var(--text-secondary)] font-medium">
  A Multi-Tool Approach to Frontend Development
</div>

<div class="mt-20 text-base tracking-wider uppercase font-mono text-[color:var(--text-muted)]">
  Will Marple &nbsp;·&nbsp; VueConf 2026
</div>

<div class="abs-br m-6 text-xs font-mono tracking-wider">
  <a href="https://vueconf.us" target="_blank" class="opacity-60 hover:opacity-100">
    vueconf.us
  </a>
</div>

<!--
Stop using one AI tool for everything. When I wrote this paper in November, I was writing it for myself first and foremost. I wondered if there were other developers out there like me who were vendor-locked into one model or perhaps one tool, one agent, one harness. I realized that while I had become proficient using Claude models and Claude harnesses, that I was vendor locked to a degree.  I'd experimented with other tools sure, but my experience with them paled compared to the reps I'd put in building real software with Claude. This talk is about sharing some of what I’ve learned on my journey to identify first principles in agentic engineering, and my conviction that one of the best things we can do in the current era is to infuse our agents with the essence of what makes us good engineers.  We can do this today in a layer that stays under out control and ownership, the agent harness.
-->

---
layout: default
class: '!justify-center'
---

<div class="speaker-intro">
  <div class="kicker">Hi, I'm</div>

  <h1 class="name">Will Marple</h1>

  <div class="role">Distinguished Engineer</div>

  <div class="company">
    <span class="company-label">at</span>
    <BaLogo />
    <span class="company-wordmark">Black&nbsp;Airplane</span>
  </div>
</div>

<style>
.speaker-intro {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  max-width: 60%;
  margin-left: 1rem;
}

.kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.name {
  font-size: 6rem !important;
  line-height: 0.95 !important;
  margin: 0 !important;
  font-weight: 700;
  color: var(--text-primary);
}

.role {
  font-size: 1.6rem;
  color: var(--text-secondary);
  font-weight: 400;
  margin-top: -0.25rem;
}

.company {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-top: 2rem;
  padding-top: 1.5rem;
  border-top: 1px solid var(--border);
  max-width: 32rem;
}

.company-label {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.company-wordmark {
  font-family: var(--font-display);
  font-size: 1.65rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}
</style>

<!--
Quick personal handoff: name, title, company. Don't dwell. The deck is the talk, not me.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="confession-slide">
  <div class="kicker">A quick confession</div>

  <p class="confession-line">
    Last <span class="month">November</span>, this was the talk:
  </p>

  <div class="pipeline">
    <div class="pipe-card">
      <div class="pipe-name">Figma&nbsp;MCP</div>
      <div class="pipe-role">design source</div>
    </div>
    <div class="pipe-arrow" aria-hidden="true">→</div>
    <div class="pipe-card">
      <div class="pipe-name">Gemini</div>
      <div class="pipe-role">design extraction</div>
    </div>
    <div class="pipe-arrow" aria-hidden="true">→</div>
    <div class="pipe-card">
      <div class="pipe-name">Claude</div>
      <div class="pipe-role">implementation</div>
    </div>
  </div>
</div>

<style>
.confession-slide {
  max-width: 62rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 2.25rem;
}

.kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.confession-line {
  font-size: 1.9rem;
  line-height: 1.35;
  color: var(--text-primary);
  margin: 0;
  font-weight: 400;
  letter-spacing: -0.01em;
}

.month {
  font-weight: 600;
  color: var(--vue-green-light);
}

.pipeline {
  display: flex;
  align-items: stretch;
  gap: 0.6rem;
  margin-top: 0.5rem;
}

.pipe-card {
  flex: 1;
  padding: 1.5rem 1.1rem;
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  align-items: center;
  justify-content: center;
  text-align: center;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.pipe-name {
  font-family: var(--font-display);
  font-size: 1.55rem;
  font-weight: 700;
  letter-spacing: -0.015em;
  color: var(--text-primary);
  white-space: nowrap;
}

.pipe-role {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.pipe-arrow {
  display: flex;
  align-items: center;
  font-family: var(--font-display);
  font-size: 1.6rem;
  font-weight: 400;
  color: var(--vue-green);
  padding: 0 0.25rem;
}
</style>

<!--
Land the kicker, then the line — slow. "Last November, this was the talk." Pause. Gesture at the diagram.

This is the SETUP, not the punchline. Don't editorialize yet. Just let them see what was promised. The deflation comes on the next slide.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="deflation-slide">
  <div class="obsolete-row">
    <div class="pipe-card-old">
      <div class="pipe-name-old">Figma&nbsp;MCP</div>
    </div>
    <div class="arrow-old" aria-hidden="true">→</div>
    <div class="pipe-card-old">
      <div class="pipe-name-old">Gemini</div>
    </div>
    <div class="arrow-old" aria-hidden="true">→</div>
    <div class="pipe-card-old">
      <div class="pipe-name-old">Claude</div>
    </div>
  </div>

  <div class="collapse-arrow" aria-hidden="true">↓</div>

  <div class="now-card">
    <div class="now-name">Claude · Opus 4.7</div>
    <div class="now-role">1M context window — all of the above, one tool</div>
  </div>

  <p class="punchline">A lot happens in AI in 6 months.</p>
</div>

<style>
.deflation-slide {
  max-width: 60rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.1rem;
}

.obsolete-row {
  display: flex;
  align-items: stretch;
  gap: 0.5rem;
  width: 100%;
}

.pipe-card-old {
  flex: 1;
  padding: 1rem 0.8rem;
  border: 1px solid var(--border-soft);
  border-radius: 0.5rem;
  background: var(--bg-elev-1);
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  position: relative;
  opacity: 0.38;
}

.pipe-card-old::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 6%;
  right: 6%;
  height: 2px;
  background: var(--code-red);
  transform: rotate(-2deg);
  opacity: 0.85;
}

.pipe-name-old {
  font-family: var(--font-display);
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--text-muted);
}

.arrow-old {
  display: flex;
  align-items: center;
  font-size: 1rem;
  color: var(--text-faint);
  padding: 0 0.25rem;
  opacity: 0.5;
}

.collapse-arrow {
  font-family: var(--font-display);
  font-size: 2rem;
  color: var(--vue-green);
  font-weight: 300;
  line-height: 1;
}

.now-card {
  padding: 1.5rem 2.5rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 35%, var(--border));
  border-radius: 0.75rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 82%, var(--vue-green) 18%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  align-items: center;
  text-align: center;
  box-shadow:
    0 0 28px color-mix(in srgb, var(--vue-green) 22%, transparent),
    inset 0 1px 0 color-mix(in srgb, white 6%, transparent);
}

.now-name {
  font-family: var(--font-display);
  font-size: 2rem;
  font-weight: 700;
  letter-spacing: -0.02em;
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.now-role {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.66rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.punchline {
  margin-top: 0.75rem;
  font-family: var(--font-display);
  font-size: 1.4rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  letter-spacing: -0.01em;
}
</style>

<!--
Visual deflation: the obsolete pipeline at the top, collapsing into one tool below. Deliver the line VERBALLY: "This was written 8 months ago. Welcome to AI." Don't read the slide — the slide is the receipt.

Pause for the laugh, then pivot.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="pivot-slide">
  <p class="pivot-line-1">AI can write code now.</p>
  <p class="pivot-line-2">
    Your previous skill is certainly still relevant, but there's a new skill in the <span class="emph">layer you build</span> around out-of-the-box AI agent capabilities.
  </p>
</div>

<style>
.pivot-slide {
  max-width: 60rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.pivot-line-1 {
  font-family: var(--font-display);
  font-size: 2.6rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  letter-spacing: -0.015em;
  line-height: 1.15;
}

.pivot-line-2 {
  font-family: var(--font-display);
  font-size: 3.1rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.015em;
  line-height: 1.15;
}

.pivot-line-2 .dim {
  color: var(--text-muted);
  font-weight: 600;
}

.pivot-line-2 .emph {
  color: var(--vue-green-light);
  font-weight: 800;
}
</style>

<!--
This is the PIVOT — from joke deflation into the positive frame the rest of the talk depends on.

DELIVERY:
- Acknowledge what the audience has already metabolized about AI's capability without dwelling on it:
  "For a couple of years now, the panic was that AI would replace us. I think we're past that conversation."
- Pause. Then state the new reality plainly:
  "AI can write code. That's just true."
- Then turn:
  "But the work didn't disappear — it moved. The new skill is in the layer we build around the model."
- Look at the room on the turn. The slide reinforces visually; you carry the energy.

WHY THIS SLIDE MATTERS:
- It's load-bearing for the whole body of the talk. The audience needs to leave this slide thinking "there's something new for me to learn" — not "I'm being replaced," not "tools come and go."
- "The layer you build around it" is the harness in plain language. Plants the concept before slide 11 names it formally.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="quote-slide">
  <blockquote class="big-quote">
    The art of live sound is the art of turning things <em>down</em>.
  </blockquote>
</div>

<style>
.quote-slide {
  max-width: 60rem;
  margin: 0 auto;
  padding: 0 2rem;
}

.quote-slide .big-quote {
  font-family: var(--font-display);
  font-size: 2.5rem;
  font-weight: 500;
  color: var(--text-primary);
  line-height: 1.3;
  letter-spacing: -0.015em;
  border-left: 3px solid var(--vue-green);
  padding: 0.25rem 0 0.25rem 2rem;
  font-style: normal;
  margin: 0;
  background: none;
}

.quote-slide .big-quote em {
  color: var(--vue-green-light);
  font-style: italic;
  font-weight: 700;
}
</style>

<!--
The audio metaphor. Sets up the talk's core idea — our job is intelligibility, not generation.

DELIVERY:
- Set up the source: "I've heard it said in the professional audio world..." Beat.
- Read the quote slowly. Let it land.
- Don't explain it here — the application comes on the next slide.

RESONANCE (probably deliver this on the NEXT slide as the bridge into "AI just turned the volume up," not here — it might be premature at the quote):
"In the age of AI agents, I think we're all looking for ways to turn down the noise and catch the true signal — to deliver value at scale without losing the thread."
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="bridge-slide">
  <p class="bridge-line-1">In many ways, AI just turned the volume up on us.</p>
  <p class="bridge-line-2">
    Time to build your own <span class="grad">control&nbsp;board</span>.
  </p>
</div>

<style>
.bridge-slide {
  max-width: 60rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.bridge-line-1 {
  font-family: var(--font-display);
  font-size: 2.6rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  letter-spacing: -0.015em;
  line-height: 1.15;
}

.bridge-line-2 {
  font-family: var(--font-display);
  font-size: 3rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.015em;
  line-height: 1.15;
}
</style>

<!--
Bridge from metaphor to the talk. "AI just turned the volume up." — meaning, more code, more output, more options, more noise.

Then the tee-up: "Time to build your own mixing board." This is your seed for the harness — though you don't name the harness yet. Just plant the metaphor.

After this slide, we enter the trap setup.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="two-modes-slide">
  <div class="modes-kicker">Two ways to fail</div>

  <div class="modes">
    <div class="mode">
      <div class="mode-num">01</div>
      <div class="mode-title">Read every line.</div>
      <div class="mode-result">Don't scale.</div>
    </div>
    <div class="mode">
      <div class="mode-num">02</div>
      <div class="mode-title">Read nothing.</div>
      <div class="mode-result">Ship dark code.</div>
    </div>
  </div>

  <p class="modes-caption">One feels responsible. The other feels irresponsible. Neither is viable or scalable.</p>
</div>

<style>
.two-modes-slide {
  max-width: 64rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.75rem;
}

.modes-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.modes {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.mode {
  padding: 1.75rem 1.5rem;
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.mode-num {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  color: var(--vue-green-light);
  opacity: 0.75;
}

.mode-title {
  font-family: var(--font-display);
  font-size: 1.7rem;
  font-weight: 700;
  letter-spacing: -0.015em;
  color: var(--text-primary);
  line-height: 1.15;
}

.mode-result {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.modes-caption {
  font-family: var(--font-display);
  font-size: 1.45rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}
</style>

<!--
The trap. Two failure modes, side-by-side. The audience recognizes themselves in one — probably one or the other.

Set up: "There are two ways to fail at this." Read the first card. Beat. Read the second. Beat.

Caption is the punch: "Both feel responsible. Neither is." Pause. This earns the thesis on the next slides (debt → harness).
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="debt-slide">
  <div class="debt-kicker">Both have names</div>

  <div class="debts">
    <div class="debt-card">
      <div class="debt-num">01</div>
      <div class="debt-name">Velocity&nbsp;debt</div>
      <div class="debt-desc">The cost of reading every line.</div>
    </div>
    <div class="debt-card">
      <div class="debt-num">02</div>
      <div class="debt-name">Comprehension&nbsp;debt</div>
      <div class="debt-desc">The cost of reading none of them.</div>
    </div>
  </div>

  <p class="debt-caption">Both compound.</p>
</div>

<style>
.debt-slide {
  max-width: 64rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.75rem;
}

.debt-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.debts {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.debt-card {
  padding: 1.75rem 1.5rem;
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.debt-num {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  color: var(--vue-green-light);
  opacity: 0.75;
}

.debt-name {
  font-family: var(--font-display);
  font-size: 1.85rem;
  font-weight: 700;
  letter-spacing: -0.015em;
  color: var(--text-primary);
  line-height: 1.1;
}

.debt-desc {
  font-family: var(--font-body);
  font-size: 0.95rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
  line-height: 1.4;
}

.debt-caption {
  font-family: var(--font-display);
  font-size: 1.45rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}
</style>

<!--
This slide names the two failure modes from the prior slide. The vocabulary is the point — "velocity debt" and "comprehension debt" should land as TERMS the audience will remember.

DELIVERY:
- "Both of these have names." Read each card.
- "Velocity debt: the cost of reading every line — you can't ship fast enough."
- "Comprehension debt: the cost of reading none of them — you can't own what you shipped."
- Beat. "Both compound." (caption lands)

The word "comprehension" is doing load-bearing work for the rest of the talk. Plant it carefully.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="thesis-slide">
  <p class="thesis-setup">Agentic engineering isn't about how much code you can produce.</p>
  <p class="thesis-payoff">
    It's about how much you can <span class="emph">responsibly&nbsp;own</span>.
  </p>
</div>

<style>
.thesis-slide {
  max-width: 64rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.thesis-setup {
  font-family: var(--font-display);
  font-size: 2.1rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  letter-spacing: -0.015em;
  line-height: 1.2;
}

.thesis-payoff {
  font-family: var(--font-display);
  font-size: 2.8rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.015em;
  line-height: 1.15;
}

.thesis-payoff .emph {
  color: var(--vue-green-light);
  font-weight: 800;
}
</style>

<!--
The thesis. Big quiet slide. This is the claim the rest of the talk has to earn.

DELIVERY:
- Read the setup line slowly. Pause.
- Then the payoff. Land on "responsibly own."
- DON'T move on quickly. This is the slide that frames everything that follows.

If this lands, the body of the talk is the operationalization. If it doesn't land, nothing after fixes it.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="harness-slide">
  <p class="harness-line">
    Engineer your own <span class="grad">harness</span>.
  </p>
  <p class="harness-sub">
    The system you build that builds the system.
  </p>
  <div class="harness-tee">↓&nbsp;&nbsp;Let&nbsp;me&nbsp;show&nbsp;you&nbsp;how</div>
</div>

<style>
.harness-slide {
  max-width: 64rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.harness-line {
  font-family: var(--font-display);
  font-size: 3.4rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.02em;
  line-height: 1.05;
}

.harness-sub {
  font-family: var(--font-body);
  font-size: 1.3rem;
  font-weight: 400;
  color: var(--text-secondary);
  margin: 0;
  line-height: 1.45;
  max-width: 36rem;
}

.harness-tee {
  margin-top: 2rem;
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.75;
}
</style>

<!--
First explicit naming of "harness" in the talk. Everything before this earned the moment. Everything after operationalizes it.

DELIVERY:
- Land the line. Heavy weight on "harness."
- Pause.
- Optional: read the subtitle ("the system you build to comprehend what you ship") — or paraphrase it from stage.
- The mono tee-up at the bottom signals to the audience that the body is about to begin. Don't read it; let it appear.

After this slide we enter §3 — the mental model (four levers + loop).
-->

---
layout: default
class: '!justify-center'
transition: fade
clicks: 5
---

<div class="levers-slide">
  <div class="lev-kicker">The shape of the harness</div>

  <div class="lev-eval" v-click="5">
    <div class="lev-eval-label">↺ &nbsp; the loop</div>
    <div class="lev-eval-name">Evaluation</div>
    <div class="lev-eval-role">closes the system — verifies the output against the spec</div>
  </div>

  <div class="levers">
    <div class="lever" v-click="1">
      <div class="lev-num">01</div>
      <div class="lev-name">Prompting</div>
      <div class="lev-role">the instruction</div>
    </div>
    <div class="lever" v-click="2">
      <div class="lev-num">02</div>
      <div class="lev-name">Context</div>
      <div class="lev-role">the working set</div>
    </div>
    <div class="lever" v-click="3">
      <div class="lev-num">03</div>
      <div class="lev-name">Memory</div>
      <div class="lev-role">what persists</div>
    </div>
    <div class="lever" v-click="4">
      <div class="lev-num">04</div>
      <div class="lev-name">Tools</div>
      <div class="lev-role">what it can do</div>
    </div>
  </div>
</div>

<style>
.levers-slide {
  max-width: 68rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.lev-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.lev-eval {
  padding: 1.25rem 2rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 35%, var(--border));
  border-radius: 0.75rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 82%, var(--vue-green) 18%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
  align-items: center;
  text-align: center;
  box-shadow:
    0 0 24px color-mix(in srgb, var(--vue-green) 20%, transparent),
    inset 0 1px 0 color-mix(in srgb, white 6%, transparent);
}

.lev-eval-label {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.lev-eval-name {
  font-family: var(--font-display);
  font-size: 1.85rem;
  font-weight: 700;
  letter-spacing: -0.015em;
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  margin: 0;
}

.lev-eval-role {
  font-family: var(--font-body);
  font-size: 0.95rem;
  color: var(--text-secondary);
  margin: 0;
}

.levers {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0.75rem;
}

.lever {
  padding: 1.5rem 1rem;
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.lev-num {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  color: var(--vue-green-light);
  opacity: 0.75;
}

.lev-name {
  font-family: var(--font-display);
  font-size: 1.55rem;
  font-weight: 700;
  letter-spacing: -0.015em;
  color: var(--text-primary);
  line-height: 1.1;
}

.lev-role {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--text-muted);
}

/* Smooth fade-in for v-click reveals on this slide */
.lever,
.lev-eval {
  transition: opacity 280ms ease-out;
}
</style>

<!--
Single-slide progressive build of the mental model. Six visible states (click 0 through click 5).

CLICK SEQUENCE:
  0 (default): Only the kicker "THE SHAPE OF THE HARNESS" is visible. Empty slots reserved.
  1. Prompting card lights up   — "the first lever is the instruction itself"
  2. Context card lights up     — "what you put in front of the model"
  3. Memory card lights up      — "what persists across sessions"
  4. Tools card lights up       — "what the model can actually do"
  5. Evaluation card appears at top — "and the whole thing only closes if you verify against the spec"

DELIVERY NOTES:
- Don't rush the clicks. Each lever needs a beat to land in the audience's head before stacking the next.
- The eval reveal at click 5 is the moment. Pause there. Then deliver: "this is the shape of the harness."
- We DELIBERATELY OMIT Orchestration here to keep the model to 4+1. It comes back as a footnote later (or in §5/§6 as needed).

VOCABULARY ANCHOR: every lever name on this slide is one the rest of the talk will refer back to. Use them by name from here on.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="floor-slide">
  <div class="floor-kicker">out of the box</div>
  <div class="floor-models">
    <div class="floor-model">GPT-5</div>
    <div class="floor-model">Claude Opus 4.7</div>
    <div class="floor-model">Gemini 3</div>
  </div>
  <div class="floor-rule" aria-hidden="true">
    <span class="floor-rule-line"></span>
    <span class="floor-rule-label">MEDIAN OUTPUT</span>
    <span class="floor-rule-line"></span>
  </div>
  <div class="floor-statement">
    <p class="floor-line-1">Every developer gets the same <span class="floor-em">median intelligence per token</span>.</p>
    <p class="floor-line-2">Same models. Same outputs. <span class="floor-em-strong">The floor is level.</span></p>
  </div>
  <p class="floor-caption">Out of the box, we&rsquo;re all equal.</p>
</div>

<style>
.floor-slide {
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  align-items: center;
  text-align: center;
}

.floor-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.floor-models {
  display: flex;
  gap: 0.6rem;
  justify-content: center;
  flex-wrap: wrap;
}

.floor-model {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.92rem;
  font-weight: 500;
  letter-spacing: 0.06em;
  color: var(--text-secondary);
  padding: 0.45rem 0.9rem;
  background: var(--bg-elev-1);
  border: 1px solid var(--border);
  border-radius: 0.4rem;
}

.floor-rule {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: center;
  gap: 1rem;
  width: 100%;
  max-width: 56rem;
}

.floor-rule-line {
  height: 1px;
  background: linear-gradient(90deg,
    transparent,
    color-mix(in srgb, var(--vue-green) 60%, transparent),
    transparent);
}

.floor-rule-label {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.floor-statement {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  max-width: 60rem;
}

.floor-line-1 {
  font-family: var(--font-display);
  font-size: 2rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  letter-spacing: -0.015em;
  line-height: 1.25;
}

.floor-line-2 {
  font-family: var(--font-display);
  font-size: 2.4rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.02em;
  line-height: 1.15;
}

.floor-em {
  color: var(--vue-green-light);
  font-weight: 700;
}

.floor-em-strong {
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.floor-caption {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--text-muted);
  margin: 0;
}
</style>

<!--
S12a · "Out of the box, we're all equal."

DELIVERY:
- "Every developer in this room has access to the same models."
- Name them. GPT-5, Claude Opus 4.7, Gemini 3. Same APIs. Same prices per token.
- "Out of the box, you get the median intelligence per token. The median output. That's the floor."
- Pause. "The floor is level. So the question becomes: what do you build above it?"
- Tee up the next slide.

NARRATIVE BEAT: sets up the harness as a differentiator, not a tool. The audience needs to feel the equal-starting-point before the next slide drives home "your harness is your edge."
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="edge-slide">
  <div class="edge-kicker">above the floor</div>
  <h1 class="edge-headline">Your harness is your <span class="edge-em">edge</span>.</h1>
  <div class="edge-grid">
    <div class="edge-card">
      <div class="edge-card-tag">PULLS THE MEDIAN UP</div>
      <div class="edge-card-body">Context, memory, tools, eval — tuned to <em>this</em> project. Median output becomes <span class="edge-card-em">your</span> output.</div>
    </div>
    <div class="edge-card">
      <div class="edge-card-tag">LIVING · BREATHING</div>
      <div class="edge-card-body">Every rep updates it. Every spec, every review, every flagged regression — your harness gets sharper.</div>
    </div>
    <div class="edge-card edge-card-emph">
      <div class="edge-card-tag">UNIQUELY YOURS</div>
      <div class="edge-card-body">Your experience, your judgment, your defaults — <span class="edge-card-em">infused into the process</span>. Nobody else has this one.</div>
    </div>
  </div>
  <p class="edge-caption">The model is a commodity. <span class="edge-em">The harness is you.</span></p>
</div>

<style>
.edge-slide {
  max-width: 78rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  align-items: center;
  text-align: center;
}

.edge-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.edge-headline {
  font-family: var(--font-display) !important;
  font-size: 3.2rem !important;
  font-weight: 700 !important;
  color: var(--text-primary) !important;
  margin: 0 !important;
  letter-spacing: -0.025em;
  line-height: 1.05;
}

.edge-em {
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.edge-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.85rem;
  width: 100%;
  margin-top: 0.5rem;
}

.edge-card {
  padding: 1.4rem 1.25rem;
  border: 1px solid var(--border);
  border-radius: 0.65rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.7rem;
  text-align: left;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.edge-card-emph {
  border-color: color-mix(in srgb, var(--vue-green-light) 38%, var(--border));
  box-shadow:
    inset 0 1px 0 color-mix(in srgb, white 5%, transparent),
    0 0 22px color-mix(in srgb, var(--vue-green) 18%, transparent);
}

.edge-card-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.edge-card-body {
  font-family: var(--font-body);
  font-size: 1rem;
  color: var(--text-secondary);
  line-height: 1.5;
}

.edge-card-body em {
  color: var(--vue-green-light);
  font-style: italic;
  font-weight: 600;
}

.edge-card-em {
  color: var(--vue-green-light);
  font-weight: 700;
}

.edge-caption {
  font-family: var(--font-display);
  font-size: 1.4rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0.5rem 0 0;
}
</style>

<!--
S12b · "Your harness is your edge."

DELIVERY:
- "Out of the box, the floor is level. The harness is what you build above it."
- Walk the three cards:
  - "Pulls the median up — context, memory, tools, eval tuned to THIS project."
  - "Living and breathing — every rep, every review, every spec — your harness gets sharper."
  - "Uniquely yours — your experience, your judgment, your defaults, infused into the process."
- Land the caption SLOWLY: "The model is a commodity. The harness is you."
- This is the line that lets the audience feel ownership of the rest of the talk. Earn the pause.

NARRATIVE BEAT: this is where the talk goes from "here's a framework" to "this is YOUR framework." Sets up the harness-visualizer reveal on the next slide — the visualizer is a place to SEE the harness, but the harness is yours.
-->

---
layout: default
class: '!justify-center text-center'
transition: fade
---

<div class="vehicle-slide">
  <div class="veh-kicker">The vehicle</div>

  <div class="veh-name"><span class="grad">harness-visualizer</span></div>

  <div class="veh-divider"></div>

  <p class="veh-tagline">Point it at a project. See its harness.</p>

  <p class="veh-meta">Built with the harness you're about to see.</p>
</div>

<style>
.vehicle-slide {
  max-width: 60rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.veh-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.veh-name {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 4.2rem;
  font-weight: 700;
  letter-spacing: -0.02em;
  line-height: 1;
  margin: 0.5rem 0;
}

.veh-divider {
  width: 3rem;
  height: 2px;
  background: linear-gradient(90deg, var(--vue-green-light), var(--vue-blue));
  margin: 0.75rem auto;
  border-radius: 999px;
}

.veh-tagline {
  font-family: var(--font-display);
  font-size: 1.7rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.01em;
}

.veh-meta {
  font-family: var(--font-body);
  font-size: 1.05rem;
  color: var(--text-secondary);
  font-style: italic;
  margin: 1rem 0 0;
  opacity: 0.85;
}
</style>

<!--
The vehicle reveal — the moment you tell the audience "the whole rest of the talk happens inside this one project."

DELIVERY:
- Land the kicker. Pause.
- Read the project name. ("harness-visualizer.")
- Read the tagline. ("Point it at a project. See its harness.")
- Then the meta-recursive line, slow: "Built with the harness you're about to see."
- That last line gets the laugh / nod. It's the recursive authenticity moment.

This is the pivot point of the talk: everything before was framing; everything after is the tour.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="shape-slide">
  <div class="shape-kicker">What a harness looks like</div>

  <pre class="shape-tree"><code><span class="shape-root">harness-visualizer/</span>
├── <span class="shape-file">AGENTS.md</span>              <span class="shape-tag tag-ctx">context · canonical</span>
├── <span class="shape-file">CLAUDE.md</span>              <span class="shape-tag tag-ctx">context · alias</span>
├── <span class="shape-file">ROADMAP.md</span>             <span class="shape-tag tag-mem">memory · progress</span>
├── <span class="shape-dir">.review/</span>              <span class="shape-tag tag-mem">memory · audit trail</span>
└── <span class="shape-dir">.claude/</span>
    ├── <span class="shape-file">settings.json</span>     <span class="shape-tag tag-hook">hooks</span>
    ├── <span class="shape-dir">skills/</span>
    │   ├── <span class="shape-dir">playwright-skill/</span>      <span class="shape-tag tag-tool">tools · eval</span>
    │   └── <span class="shape-dir">implementation-skill/</span>  <span class="shape-tag tag-tool">tools</span>
    └── <span class="shape-dir">plugins/</span>
        ├── <span class="shape-dir">spec-gen/</span>      <span class="shape-tag tag-ctx">context · multi-agent</span>
        └── <span class="shape-dir">claude-build/</span>  <span class="shape-tag tag-tool">tools · eval</span></code></pre>

  <p class="shape-caption">Files on disk. Nothing magic. <span class="shape-em">You can see all of it.</span></p>
</div>

<style>
.shape-slide {
  max-width: 70rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.shape-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.shape-tree {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.92rem;
  line-height: 1.7;
  color: var(--text-secondary);
  background: var(--bg-elev-1);
  border: 1px solid var(--border-soft);
  border-radius: 0.75rem;
  padding: 1.5rem 1.75rem;
  margin: 0;
  overflow: hidden;
}

.shape-root { color: var(--vue-green-light); font-weight: 700; }
.shape-dir { color: var(--text-primary); font-weight: 600; }
.shape-file { color: var(--text-primary); }

.shape-tag {
  display: inline-block;
  margin-left: 1.25rem;
  padding: 0.1em 0.55em;
  border-radius: 0.3em;
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  border: 1px solid;
}

.tag-ctx  { color: #82aaff; border-color: color-mix(in srgb, #82aaff 30%, transparent); background: color-mix(in srgb, #82aaff 8%, transparent); }
.tag-mem  { color: #c792ea; border-color: color-mix(in srgb, #c792ea 30%, transparent); background: color-mix(in srgb, #c792ea 8%, transparent); }
.tag-tool { color: #ffcb6b; border-color: color-mix(in srgb, #ffcb6b 30%, transparent); background: color-mix(in srgb, #ffcb6b 8%, transparent); }
.tag-hook { color: #f78c6c; border-color: color-mix(in srgb, #f78c6c 30%, transparent); background: color-mix(in srgb, #f78c6c 8%, transparent); }

.shape-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}

.shape-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
The "harness as files" moment. The audience sees the harness isn't magic — it's a file tree.

DELIVERY:
- "This is the root of harness-visualizer. The harness is just files on disk."
- Walk through the four colors: blue = context, purple = memory, yellow = tools, orange = hooks.
- The closing line is important: "You can see all of it." — this is the antidote to "AI is a black box."
- This slide primes the next four sections — one lever per file/directory color.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="viz-slide">
  <div class="viz-kicker">harness-visualizer · in motion</div>
  <div class="viz-shot">
  <img :src="`${$slidev.configs.base || '/'}screenshots/agents-expanded.png`" alt="harness-visualizer showing the agents view with claude-code expanded" />
</div>
</div>

<style>
.viz-slide {
  max-width: 80rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: stretch;
}

.viz-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.viz-shot {
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  overflow: hidden;
  background: var(--bg-elev-1);
  aspect-ratio: 16 / 8.5;
  box-shadow:
    0 12px 40px rgba(0, 0, 0, 0.35),
    0 0 28px color-mix(in srgb, var(--vue-green) 8%, transparent);
}

.viz-shot img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: top center;
}

.viz-caption {
  font-family: var(--font-display);
  font-size: 1.15rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0;
  text-align: center;
}

.viz-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
S14a · "harness-visualizer in motion." The recursive-authenticity hook.

DELIVERY:
- "Here it is, running, pointed at its own repo."
- Pause. Let the audience read the screenshot.
- "Twelve artifacts, 47k tokens, 2 flagged issues. That's claude-code's surface in this project."
- "Today's tour is what this app surfaces."

NOTE: Screenshot at public/screenshots/agents-expanded.png — re-capture closer to talk day for freshness.
-->

---
layout: default
class: '!justify-center'
transition: fade
clicks: 2
---

<div class="lenses-slide">
  <div class="lenses-kicker">three lenses · one source of truth</div>

  <div class="lenses-tabs">
    <div class="lenses-tab" :class="{ active: $clicks === 0 }">
      <span class="lenses-tab-num">01</span>
      <span class="lenses-tab-name">Agents</span>
    </div>
    <div class="lenses-tab" :class="{ active: $clicks === 1 }">
      <span class="lenses-tab-num">02</span>
      <span class="lenses-tab-name">Issues</span>
    </div>
    <div class="lenses-tab" :class="{ active: $clicks === 2 }">
      <span class="lenses-tab-num">03</span>
      <span class="lenses-tab-name">Table</span>
    </div>
  </div>

  <div class="lenses-stage">
    <div class="lens-shot" v-show="$clicks === 0">
      <img :src="`${$slidev.configs.base || '/'}screenshots/agents-view.png`" alt="Agents view" />
      <p class="lens-cap"><span class="lens-cap-key">Agents</span> · per-tool view: cascade pattern, token total, configured artifacts, issues.</p>
    </div>
    <div class="lens-shot" v-show="$clicks === 1">
      <img :src="`${$slidev.configs.base || '/'}screenshots/issues-view.png`" alt="Issues view" />
      <p class="lens-cap"><span class="lens-cap-key">Issues</span> · status flags: oversize, stale, conflict, orphan — plus token-budget warnings.</p>
    </div>
    <div class="lens-shot" v-show="$clicks === 2">
      <img :src="`${$slidev.configs.base || '/'}screenshots/table-view.png`" alt="Table view" />
      <p class="lens-cap"><span class="lens-cap-key">Table</span> · sortable inventory: every artifact, scope, path, activation, token count.</p>
    </div>
  </div>
</div>

<style>
.lenses-slide {
  max-width: 80rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.lenses-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.lenses-tabs {
  display: flex;
  gap: 0.5rem;
  padding: 0.4rem;
  background: var(--bg-elev-1);
  border: 1px solid var(--border);
  border-radius: 0.6rem;
}

.lenses-tab {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.55rem;
  padding: 0.6rem 0.85rem;
  border-radius: 0.4rem;
  background: transparent;
  transition: background-color 200ms ease, color 200ms ease, box-shadow 200ms ease;
  color: var(--text-muted);
}

.lenses-tab.active {
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-2) 78%, var(--vue-green) 22%) 0%,
      var(--bg-elev-2) 100%);
  color: var(--text-primary);
  box-shadow:
    inset 0 1px 0 color-mix(in srgb, white 5%, transparent),
    0 0 14px color-mix(in srgb, var(--vue-green) 14%, transparent);
}

.lenses-tab-num {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.14em;
  color: inherit;
  opacity: 0.6;
}

.lenses-tab.active .lenses-tab-num {
  color: var(--vue-green-light);
  opacity: 1;
}

.lenses-tab-name {
  font-family: var(--font-display);
  font-size: 1.15rem;
  font-weight: 700;
  letter-spacing: -0.01em;
}

.lenses-stage {
  position: relative;
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  overflow: hidden;
  background: var(--bg-elev-1);
  aspect-ratio: 16 / 8.5;
  box-shadow:
    0 12px 36px rgba(0, 0, 0, 0.32),
    0 0 26px color-mix(in srgb, var(--vue-green) 6%, transparent);
}

.lens-shot {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
}

.lens-shot img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: top center;
}

.lens-cap {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  margin: 0;
  padding: 0.85rem 1.25rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-base) 0%, transparent) 0%,
      color-mix(in srgb, var(--bg-base) 85%, transparent) 50%,
      color-mix(in srgb, var(--bg-base) 95%, transparent) 100%);
  font-family: var(--font-body);
  font-size: 1rem;
  color: var(--text-secondary);
  line-height: 1.45;
}

.lens-cap-key {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  margin-right: 0.35rem;
}
</style>

<!--
S14b · "Three lenses, one source of truth." Progressive reveal — one large shot per click.

CLICKS:
  0 (default): Agents tab active, agents-view screenshot
  1:           Issues tab active, issues-view screenshot
  2:           Table tab active, table-view screenshot

DELIVERY:
- Land the kicker. "Same data, three views."
- Click 0 — Agents: "Per-tool view. You see at a glance: which agents are configured, what they're carrying, what's flagged."
- Click 1 — Issues: "What needs attention. Token budget warnings, oversize files, stale entries — surfaced together."
- Click 2 — Table: "Raw inventory. Sort by scope, by tokens, by activation. The power-user lens."
- "Today we're walking the data, not the views. The views are the demo at the end."
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="skip-slide">
  <div class="skip-kicker">First stop: Prompting</div>

  <p class="skip-line">You're already good at this.</p>

  <p class="skip-sub">The interesting work is downstream.</p>
</div>

<style>
.skip-slide {
  max-width: 56rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.skip-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.skip-line {
  font-family: var(--font-display);
  font-size: 3rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.015em;
  line-height: 1.1;
}

.skip-sub {
  font-family: var(--font-body);
  font-size: 1.25rem;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}
</style>

<!--
The gracious skip. Acknowledges that prompting is the lever the audience already pulls — no need to belabor it.

DELIVERY:
- "First stop on the tour: prompting. You're already good at this." Smile.
- "I'm walking past it. The interesting work is downstream."
- Then immediately advance to Context.
- 15-20 seconds total. Don't dwell.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="budget-slide">
  <div class="budget-kicker">02 · Context — the working set right now</div>
  <div class="budget-bar">
    <div class="budget-zone budget-always">
      <div class="budget-zone-label">always-loaded</div>
      <div class="budget-zone-name">cascade</div>
      <div class="budget-zone-files">AGENTS.md · CLAUDE.md</div>
    </div>
    <div class="budget-zone budget-ondemand">
      <div class="budget-zone-label">on-demand</div>
      <div class="budget-zone-name">retrieved</div>
      <div class="budget-zone-files">conventions docs · nested rules files · specs · skills</div>
    </div>
  </div>
  <p class="budget-caption">Context management is about breaking things down so the agent loads <span class="budget-em">only what&rsquo;s relevant to the task at hand</span>.</p>
</div>

<style>
.budget-slide {
  max-width: 78rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.budget-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.budget-bar {
  display: grid;
  grid-template-columns: 1fr 1.4fr;
  gap: 4px;
  border-radius: 0.5rem;
  overflow: hidden;
  border: 1px solid var(--border);
}

.budget-zone {
  padding: 1.5rem 1.25rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.budget-always {
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 82%, var(--vue-green) 18%) 0%,
      var(--bg-elev-1) 100%);
}

.budget-ondemand {
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 88%, var(--vue-blue) 12%) 0%,
      var(--bg-elev-1) 100%);
}

.budget-zone-label {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 500;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.budget-always .budget-zone-label { color: var(--vue-green-light); }
.budget-ondemand .budget-zone-label { color: #82aaff; }

.budget-zone-name {
  font-family: var(--font-display);
  font-size: 1.45rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

.budget-zone-files {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  letter-spacing: 0.02em;
  color: var(--text-secondary);
  line-height: 1.5;
}

.budget-caption {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0;
}

.budget-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 700;
}
</style>

<!--
S15b · "Context = the working set right now." Sets up the budget framing for the whole Context section.

DELIVERY:
- "Context isn't everything the agent COULD know. It's what loads right now."
- Walk the three zones: always-loaded, on-demand, never.
- "Engineering context means deciding what goes where."
- Tee up AGENTS.md as the prime example of always-loaded.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="ctx-slide">
  <div class="ctx-kicker">02 · Context — the canonical anchor</div>

  <div class="ctx-grid">
    <div class="ctx-snippet">
      <div class="ctx-file-bar">
        <span class="ctx-file-name">AGENTS.md</span>
        <span class="ctx-file-meta">285 lines · single source of truth</span>
      </div>
      <div class="ctx-code">
        <div class="ctx-line ctx-h"># Project constitution</div>
        <div class="ctx-line ctx-h">## Conventions</div>
        <div class="ctx-line">Source layout, naming, error</div>
        <div class="ctx-line">codes, security envelope.</div>
        <div class="ctx-spacer"></div>
        <div class="ctx-line ctx-h">## Spec workflow</div>
        <div class="ctx-line">discovery → requirements →</div>
        <div class="ctx-line">design → tasks → review.</div>
        <div class="ctx-spacer"></div>
        <div class="ctx-line ctx-h">## Harness taxonomy</div>
        <div class="ctx-line">Context · Memory · Tools ·</div>
        <div class="ctx-line">Eval — and how they compose.</div>
      </div>
    </div>
    <div class="ctx-explain">
      <p class="ctx-pt">One file every agent reads first.</p>
      <p class="ctx-pt">Tool-agnostic — Claude, Cursor, Codex all anchor here.</p>
      <p class="ctx-pt">When it changes, the project's posture changes.</p>
    </div>
  </div>
</div>

<style>
.ctx-slide {
  max-width: 70rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.ctx-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.ctx-grid {
  display: grid;
  grid-template-columns: 1.1fr 1fr;
  gap: 1.5rem;
  align-items: start;
}

.ctx-snippet {
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  background: var(--bg-elev-1);
  overflow: hidden;
}

.ctx-file-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem 0.9rem;
  background: var(--bg-elev-2);
  border-bottom: 1px solid var(--border-soft);
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.68rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.ctx-file-name { color: var(--text-primary); font-weight: 600; }
.ctx-file-meta { color: var(--text-muted); }

.ctx-code {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  line-height: 1.55;
  color: var(--text-secondary);
  padding: 0.9rem 1.1rem;
  margin: 0;
}

.ctx-line { white-space: pre; }
.ctx-h { color: var(--vue-green-light); font-weight: 600; }
.ctx-spacer { height: 0.5rem; }

.ctx-explain {
  display: flex;
  flex-direction: column;
  gap: 1.1rem;
  padding-top: 0.5rem;
}

.ctx-pt {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0;
  line-height: 1.35;
  letter-spacing: -0.01em;
}

.ctx-pt + .ctx-pt::before {
  content: '';
  display: block;
  width: 1.5rem;
  height: 1px;
  background: var(--vue-green);
  margin-bottom: 1.1rem;
  opacity: 0.5;
}
</style>

<!--
Context lever, stop 1: AGENTS.md as the project's source of truth.

DELIVERY:
- "Context starts with one file. AGENTS.md — the project's constitution."
- "Every agent in the harness reads this first. Tool-agnostic — Claude reads it, Cursor reads it, Codex reads it."
- Walk the three points on the right.
- The line that should land: "When it changes, the project's posture changes." — context engineering = active editorial work.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="inside-slide">
  <div class="inside-kicker">02 · Context — inside AGENTS.md</div>
  <div class="inside-grid">
    <div class="inside-cell"><span class="inside-h">What this project is</span><span class="inside-d">scope, audience, NDA</span></div>
    <div class="inside-cell"><span class="inside-h">Stack</span><span class="inside-d">packages + roles</span></div>
    <div class="inside-cell"><span class="inside-h">Repo layout</span><span class="inside-d">tree, ownership</span></div>
    <div class="inside-cell"><span class="inside-h">Harness layer taxonomy</span><span class="inside-d">the data model</span></div>
    <div class="inside-cell"><span class="inside-h">Diagnostic codes</span><span class="inside-d">stable severity map</span></div>
    <div class="inside-cell inside-cell-bold"><span class="inside-h">Security rules</span><span class="inside-d">non-negotiable</span></div>
    <div class="inside-cell"><span class="inside-h">Conventions</span><span class="inside-d">TS · Vue · backend</span></div>
    <div class="inside-cell"><span class="inside-h">Quality gates</span><span class="inside-d">typecheck · lint · test</span></div>
    <div class="inside-cell"><span class="inside-h">Spec workflow</span><span class="inside-d">discovery → tasks</span></div>
    <div class="inside-cell"><span class="inside-h">Roadmap</span><span class="inside-d">phase status</span></div>
    <div class="inside-cell"><span class="inside-h">Out of scope</span><span class="inside-d">deliberate non-goals</span></div>
    <div class="inside-cell"><span class="inside-h">Working agreement</span><span class="inside-d">how agents behave</span></div>
  </div>
  <p class="inside-caption">Every agent reads this. <span class="inside-em">When it changes, the project&rsquo;s posture changes.</span></p>
</div>

<style>
.inside-slide {
  max-width: 80rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.inside-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.inside-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0.6rem;
}

.inside-cell {
  padding: 0.9rem 1rem;
  border: 1px solid var(--border);
  border-radius: 0.5rem;
  background: var(--bg-elev-1);
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.inside-cell-bold {
  border-color: color-mix(in srgb, #f07178 28%, var(--border));
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, #f07178 8%) 0%,
      var(--bg-elev-1) 100%);
}

.inside-h {
  font-family: var(--font-display);
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
}

.inside-cell-bold .inside-h { color: #f4a3a8; }

.inside-d {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  letter-spacing: 0.05em;
  color: var(--text-muted);
}

.inside-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0;
}

.inside-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
S16a · "Inside AGENTS.md." Concrete look at what's actually in the canonical file.

DELIVERY:
- "Here's what's in mine. Twelve sections."
- Highlight the Security rules card (the bold one) — "the only one I really call non-negotiable."
- "Every agent loads this. So when the rules change, every agent's posture changes."
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="enough-slide">
  <div class="enough-kicker">02 · Context — when one file isn&rsquo;t enough</div>

  <div class="enough-top">
    <div class="enough-anchor">
      <div class="enough-anchor-label">repo-wide</div>
      <div class="enough-anchor-name"><code>AGENTS.md</code></div>
      <div class="enough-anchor-desc">The constitution. One file, every agent.</div>
    </div>
  </div>

  <div class="enough-but">but&hellip;</div>

  <div class="enough-grid">
    <div class="enough-ws">
      <div class="enough-ws-name">backend/</div>
      <div class="enough-ws-tag">Express · Socket.IO · chokidar</div>
    </div>
    <div class="enough-ws">
      <div class="enough-ws-name">frontend/</div>
      <div class="enough-ws-tag">Vue 3 · Pinia · Tailwind</div>
    </div>
    <div class="enough-ws">
      <div class="enough-ws-name">shared/</div>
      <div class="enough-ws-tag">zod · TS types · event maps</div>
    </div>
  </div>

  <p class="enough-caption">Every workspace has its own grain.</p>
</div>

<style>
.enough-slide {
  max-width: 64rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.1rem;
  align-items: center;
  text-align: center;
}

.enough-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.enough-top {
  width: 100%;
  display: flex;
  justify-content: center;
}

.enough-anchor {
  padding: 1.35rem 2rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 35%, var(--border));
  border-radius: 0.75rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 82%, var(--vue-green) 18%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  align-items: center;
  min-width: 24rem;
  box-shadow:
    0 0 22px color-mix(in srgb, var(--vue-green) 18%, transparent),
    inset 0 1px 0 color-mix(in srgb, white 5%, transparent);
}

.enough-anchor-label {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.enough-anchor-name code {
  font-family: var(--font-mono);
  font-size: 1.55rem;
  font-weight: 700;
  color: var(--text-primary);
  padding: 0.18em 0.65em;
  margin: 0 0.18em;
}

.enough-anchor-desc {
  font-family: var(--font-body);
  font-size: 0.95rem;
  color: var(--text-secondary);
}

.enough-but {
  font-family: var(--font-display);
  font-size: 1.4rem;
  font-style: italic;
  color: var(--text-muted);
  font-weight: 400;
}

.enough-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.8rem;
  width: 100%;
}

.enough-ws {
  padding: 1.1rem 1rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background: var(--bg-elev-1);
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
  align-items: center;
}

.enough-ws-name {
  font-family: var(--font-mono);
  font-size: 1.15rem;
  font-weight: 700;
  color: var(--text-primary);
}

.enough-ws-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  letter-spacing: 0.08em;
  color: var(--text-muted);
}

.enough-caption {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 500;
  color: var(--text-primary);
  font-style: italic;
  margin: 0.25rem 0 0;
}
</style>

<!--
S16b · "When AGENTS.md isn't enough." Sets up the need for progressive disclosure docs.

DELIVERY:
- "AGENTS.md is the constitution. One file, every agent reads it."
- "But the backend isn't the frontend isn't the shared layer."
- "Each workspace has its own grain. Trying to fit it all in AGENTS.md bloats the file."
- Pause. Tee up the next slide: "So we layer."
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="pd-tree-slide">
  <div class="pd-tree-kicker">02 · Context — progressive disclosure, made of files</div>

  <div class="pd-tree-grid">
    <div class="pd-tree-card">
      <div class="pd-tree-bar"><span class="pd-tree-path">backend/docs/conventions/</span></div>
      <div class="pd-tree-body">
        <div class="pd-tree-row pd-tree-dir">patterns/<span class="pd-tree-note">HOW we build</span></div>
        <div class="pd-tree-row pd-tree-dir">features/<span class="pd-tree-note">WHAT we ship</span></div>
      </div>
    </div>
    <div class="pd-tree-card">
      <div class="pd-tree-bar"><span class="pd-tree-path">frontend/docs/conventions/</span></div>
      <div class="pd-tree-body">
        <div class="pd-tree-row pd-tree-dir">patterns/<span class="pd-tree-note">HOW we build</span></div>
        <div class="pd-tree-row pd-tree-dir">features/<span class="pd-tree-note">WHAT we ship</span></div>
      </div>
    </div>
    <div class="pd-tree-card">
      <div class="pd-tree-bar"><span class="pd-tree-path">shared/docs/conventions/</span></div>
      <div class="pd-tree-body">
        <div class="pd-tree-row pd-tree-dir">patterns/<span class="pd-tree-note">HOW we build</span></div>
        <div class="pd-tree-row pd-tree-dim">&mdash;</div>
      </div>
    </div>
  </div>

  <div class="pd-tree-legend">
    <div class="pd-tree-leg"><span class="pd-tree-leg-key">patterns</span><span class="pd-tree-leg-val">reusable idioms</span></div>
    <div class="pd-tree-leg"><span class="pd-tree-leg-key">features</span><span class="pd-tree-leg-val">domain capabilities</span></div>
  </div>

  <p class="pd-tree-caption">Agents load only what&rsquo;s relevant to where they&rsquo;re working.</p>
</div>

<style>
.pd-tree-slide {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.pd-tree-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.pd-tree-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.85rem;
}

.pd-tree-card {
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background: var(--bg-elev-1);
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.pd-tree-bar {
  padding: 0.5rem 0.85rem;
  background: var(--bg-elev-2);
  border-bottom: 1px solid var(--border-soft);
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  letter-spacing: 0.04em;
}

.pd-tree-path { color: var(--vue-green-light); font-weight: 600; }

.pd-tree-body {
  padding: 0.85rem 1rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  color: var(--text-primary);
}

.pd-tree-row {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
}

.pd-tree-dir { color: var(--text-primary); font-weight: 600; }
.pd-tree-dim { color: var(--text-faint); }

.pd-tree-note {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.6rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.pd-tree-legend {
  display: flex;
  justify-content: center;
  gap: 2rem;
}

.pd-tree-leg {
  display: flex;
  align-items: baseline;
  gap: 0.5rem;
}

.pd-tree-leg-key {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.pd-tree-leg-val {
  font-family: var(--font-body);
  font-size: 0.9rem;
  color: var(--text-secondary);
  font-style: italic;
}

.pd-tree-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0;
}
</style>

<!--
S16c · "Progressive disclosure, made of files." The structure of the docs system.

DELIVERY:
- "Each workspace gets its own conventions folder."
- "Patterns are HOW you build — reusable idioms. Express handler shape. Pinia store layout."
- "Features are WHAT you've shipped — the scanner, the manifest emitter, the agent panels."
- "Agents only load what's relevant to where they're working." — that's the disclosure win.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="photo-slide">
  <div class="photo-kicker">02 · Context — photo-accurate, not generic</div>

  <div class="photo-grid">
    <div class="photo-card photo-bad">
      <div class="photo-tag">GENERIC TEMPLATE</div>
      <div class="photo-quote">&ldquo;Vue 3 components should use the Composition API. Use Pinia for state management. Prefer scoped styles for component isolation&hellip;&rdquo;</div>
      <div class="photo-foot">Could be any project. Cites nothing.</div>
    </div>
    <div class="photo-card photo-good">
      <div class="photo-tag">GENERATED — REAL EVIDENCE</div>
      <div class="photo-doc">
        <div class="photo-line photo-h">&#35;&#35; Pattern</div>
        <div class="photo-line">Routes wrap handlers in <code>safeAsync()</code>.</div>
        <div class="photo-spacer"></div>
        <div class="photo-line photo-h">&#35;&#35; Evidence</div>
        <div class="photo-line photo-ev">backend/src/routes/scanner.ts:42</div>
        <div class="photo-line photo-ev">backend/src/routes/manifest.ts:18</div>
        <div class="photo-line photo-ev">backend/src/routes/browse.ts:27</div>
      </div>
      <div class="photo-foot">You can navigate to where the rule lives.</div>
    </div>
  </div>

  <p class="photo-caption">No invented patterns. <span class="photo-em">If it&rsquo;s in the doc, it&rsquo;s in the code.</span></p>
</div>

<style>
.photo-slide {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.photo-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.photo-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.photo-card {
  padding: 1.25rem 1.15rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  display: flex;
  flex-direction: column;
  gap: 0.7rem;
}

.photo-bad {
  background: var(--bg-elev-1);
  opacity: 0.7;
}

.photo-bad .photo-quote {
  color: var(--text-muted);
  font-style: italic;
}

.photo-good {
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 88%, var(--vue-green) 12%) 0%,
      var(--bg-elev-1) 100%);
  border-color: color-mix(in srgb, var(--vue-green-light) 30%, var(--border));
  box-shadow: 0 0 18px color-mix(in srgb, var(--vue-green) 14%, transparent);
}

.photo-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.photo-good .photo-tag { color: var(--vue-green-light); }

.photo-quote {
  font-family: var(--font-display);
  font-size: 1.15rem;
  line-height: 1.45;
  color: var(--text-secondary);
}

.photo-doc {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.82rem;
  line-height: 1.55;
  background: var(--bg-elev-2);
  border: 1px solid var(--border-soft);
  border-radius: 0.4rem;
  padding: 0.8rem 0.95rem;
  color: var(--text-secondary);
}

.photo-line { white-space: pre; }
.photo-h { color: var(--vue-green-light); font-weight: 600; margin-top: 0.1rem; }
.photo-ev { color: var(--code-cyan); font-size: 0.78rem; }
.photo-spacer { height: 0.4rem; }

.photo-doc code {
  font-family: var(--font-mono);
  font-size: 0.95em;
  color: var(--code-cyan);
  background: transparent;
  border: none;
  padding: 0;
}

.photo-foot {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.66rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  color: var(--text-muted);
}

.photo-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0;
}

.photo-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
S16d · "Photo-accurate, not generic." The single most distinctive thing about these docs.

DELIVERY:
- Left card is the bad version — what most "convention docs" look like. Could apply anywhere. Cites nothing.
- Right card is the real thing — patterns with path:line evidence pulled from this codebase.
- Land: "No invented patterns. If it's in the doc, it's in the code." — that's the trust contract.
- This is the only slide in the deck that uses a real path:line snippet (decision logged in slides-build-plan.md). Resist the temptation to swap for stylized.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="auth-slide">
  <div class="auth-kicker">02 · Context — the docs author themselves</div>

  <div class="auth-phases">
    <div class="auth-phase">
      <div class="auth-num">01</div>
      <div class="auth-name">discover</div>
      <div class="auth-desc">Workspaces classified. Patterns + features detected.</div>
      <div class="auth-meta">heuristic · no LLM</div>
    </div>
    <div class="auth-arrow">→</div>
    <div class="auth-phase">
      <div class="auth-num">02</div>
      <div class="auth-name">scaffold</div>
      <div class="auth-desc">Folders + READMEs created. Idempotent.</div>
      <div class="auth-meta">filesystem</div>
    </div>
    <div class="auth-arrow">→</div>
    <div class="auth-phase auth-phase-author">
      <div class="auth-num">03</div>
      <div class="auth-name">author</div>
      <div class="auth-desc">Worker pool writes pattern + feature docs with evidence.</div>
      <div class="auth-meta">parallel · bounded · LLM</div>
    </div>
  </div>

  <div class="auth-stamps">
    <div class="auth-stamp">re-runnable</div>
    <div class="auth-stamp">symbol-level anchors</div>
    <div class="auth-stamp">HIGH / MEDIUM / LOW staleness bands</div>
  </div>

  <p class="auth-caption">When code changes, re-run. <span class="auth-em">The docs catch up to the code.</span></p>
</div>

<style>
.auth-slide {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.auth-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.auth-phases {
  display: grid;
  grid-template-columns: 1fr auto 1fr auto 1fr;
  gap: 0.5rem;
  align-items: stretch;
}

.auth-phase {
  padding: 1.25rem 1.1rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.auth-phase-author {
  border-color: color-mix(in srgb, var(--vue-green-light) 35%, var(--border));
  box-shadow:
    inset 0 1px 0 color-mix(in srgb, white 5%, transparent),
    0 0 18px color-mix(in srgb, var(--vue-green) 16%, transparent);
}

.auth-num {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  color: var(--vue-green-light);
  opacity: 0.75;
}

.auth-name {
  font-family: var(--font-display);
  font-size: 1.45rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  color: var(--text-primary);
  line-height: 1.05;
}

.auth-desc {
  font-family: var(--font-body);
  font-size: 0.95rem;
  color: var(--text-secondary);
  line-height: 1.4;
}

.auth-meta {
  margin-top: auto;
  padding-top: 0.45rem;
  border-top: 1px solid var(--border-soft);
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.6rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.auth-arrow {
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-display);
  font-size: 1.35rem;
  color: var(--vue-green);
  opacity: 0.65;
}

.auth-stamps {
  display: flex;
  justify-content: center;
  gap: 0.6rem;
  flex-wrap: wrap;
}

.auth-stamp {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  padding: 0.3rem 0.65rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 25%, var(--border));
  border-radius: 0.35rem;
  background: var(--bg-elev-1);
}

.auth-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0;
}

.auth-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
S16e · "The docs author themselves." Closes the auto-authoring story.

DELIVERY:
- "Three phases. Discover is heuristics — no LLM, just looking at package.json and the file tree."
- "Scaffold creates the folders. Idempotent — re-runnable."
- "Author is the LLM work. Bounded worker pool — up to 12 doc-authors in parallel. Each writes ONE doc from a brief."
- Stamps below reinforce the discipline.
- Caption: "When code changes, re-run. The docs catch up to the code."
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="prec-slide">
  <div class="prec-kicker">02 · Context — observational, not normative</div>

  <div class="prec-stack">
    <div class="prec-layer prec-layer-agents">
      <div class="prec-layer-tag">NORMATIVE · human-authored</div>
      <div class="prec-layer-name"><code>AGENTS.md</code></div>
      <div class="prec-layer-role">Rules. Principles. Non-negotiables.</div>
    </div>
    <div class="prec-conflict">
      <span class="prec-cflag">⚠ conflict?</span>
      <span class="prec-cnote">flag for human review — never silently override</span>
    </div>
    <div class="prec-layer prec-layer-gen">
      <div class="prec-layer-tag">OBSERVATIONAL · agent-authored</div>
      <div class="prec-layer-name">generated convention docs</div>
      <div class="prec-layer-role">Cited evidence. What the code does today.</div>
    </div>
  </div>

  <p class="prec-caption">The agent describes. <span class="prec-em">The human decides what the rules should be.</span></p>
</div>

<style>
.prec-slide {
  max-width: 64rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.prec-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.prec-stack {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  gap: 0.5rem;
}

.prec-layer {
  padding: 1.5rem 1.75rem;
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: center;
  text-align: center;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
}

.prec-layer-agents {
  border-color: color-mix(in srgb, var(--vue-green-light) 38%, var(--border));
  box-shadow:
    inset 0 1px 0 color-mix(in srgb, white 5%, transparent),
    0 0 22px color-mix(in srgb, var(--vue-green) 16%, transparent);
}

.prec-layer-gen {
  border-color: color-mix(in srgb, #82aaff 28%, var(--border));
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, #82aaff 8%) 0%,
      var(--bg-elev-1) 100%);
}

.prec-layer-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 500;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.prec-layer-agents .prec-layer-tag { color: var(--vue-green-light); }
.prec-layer-gen .prec-layer-tag { color: #82aaff; }

.prec-layer-name {
  font-family: var(--font-display);
  font-size: 1.85rem;
  font-weight: 700;
  letter-spacing: -0.015em;
  color: var(--text-primary);
  line-height: 1;
}

.prec-layer-name code {
  font-family: var(--font-mono);
  font-size: 0.95em;
  color: var(--text-primary);
  padding: 0.18em 0.65em;
  margin: 0 0.18em;
}

.prec-layer-role {
  font-family: var(--font-body);
  font-size: 1rem;
  color: var(--text-secondary);
}

.prec-conflict {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.2rem;
  padding: 0.45rem 1rem;
  margin: 0.1rem auto;
}

.prec-cflag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: #ffcb6b;
}

.prec-cnote {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.66rem;
  letter-spacing: 0.05em;
  color: var(--text-muted);
}

.prec-caption {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0;
}

.prec-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
S16f · "Observational, not normative." The precedence rule. Pairs with S23a (the reviewer story).

DELIVERY:
- "Two layers. AGENTS.md is normative — the rules I curate."
- "The generated docs are observational — agent-authored, evidence-cited."
- "When they conflict, the agent FLAGS — never overrides."
- Caption: "The agent describes. The human decides what the rules should be."
- This is the rule that the reviewer enforced (S23a callback later).
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="pd-slide">
  <div class="pd-kicker">02 · Context — the spec pipeline</div>
  <div class="pd-research">
    <div class="pd-research-label">parallel research</div>
    <div class="pd-research-chips">
      <span class="pd-chip">research-lead</span>
      <span class="pd-chip">integration-researcher</span>
      <span class="pd-chip">codebase-explorer</span>
    </div>
  </div>
  <div class="pd-fanin" aria-hidden="true">
    <span class="pd-fanline"></span>
    <span class="pd-fanarrow">↓</span>
  </div>
  <div class="pd-flow">
    <div class="pd-card pd-card-discovery">
      <div class="pd-num">01</div>
      <div class="pd-name">discovery</div>
      <div class="pd-note">codebase &amp; constraints</div>
    </div>
    <div class="pd-arrow">→</div>
    <div class="pd-card">
      <div class="pd-num">02</div>
      <div class="pd-name">requirements</div>
      <div class="pd-note">user-facing intent</div>
    </div>
    <div class="pd-arrow">→</div>
    <div class="pd-card">
      <div class="pd-num">03</div>
      <div class="pd-name">design</div>
      <div class="pd-note">architecture &amp; trade-offs</div>
    </div>
    <div class="pd-arrow">→</div>
    <div class="pd-card">
      <div class="pd-num">04</div>
      <div class="pd-name">tasks</div>
      <div class="pd-note">the implementation surface</div>
    </div>
  </div>
  <p class="pd-caption">Parallel research fans in. <span class="pd-em">One agent runs the pipeline</span> — each artifact narrows the next.</p>
</div>

<style>
.pd-slide {
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.pd-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.pd-research {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  align-items: center;
  padding: 1rem 1.25rem;
  border: 1px dashed color-mix(in srgb, var(--vue-green-light) 30%, var(--border));
  border-radius: 0.75rem;
  background: color-mix(in srgb, var(--bg-elev-1) 90%, var(--vue-green) 10%);
}

.pd-research-label {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.pd-research-chips {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  justify-content: center;
}

.pd-chip {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.8rem;
  font-weight: 500;
  color: var(--text-primary);
  padding: 0.35rem 0.7rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 25%, var(--border));
  border-radius: 0.4rem;
  background: var(--bg-elev-2);
}

.pd-fanin {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.2rem;
  margin: -0.4rem 0;
  color: var(--vue-green);
  font-family: var(--font-display);
  font-size: 1.4rem;
  position: relative;
}

.pd-fanline {
  width: 1px;
  height: 0.5rem;
  background: var(--vue-green);
  opacity: 0.6;
}

.pd-fanarrow {
  line-height: 1;
}

.pd-card-discovery {
  border-color: color-mix(in srgb, var(--vue-green-light) 40%, var(--border)) !important;
  box-shadow: 0 0 18px color-mix(in srgb, var(--vue-green) 15%, transparent);
}

.pd-headline {
  font-family: var(--font-display);
  font-size: 1.85rem;
  font-weight: 600;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.015em;
}

.pd-flow {
  display: grid;
  grid-template-columns: 1fr auto 1fr auto 1fr auto 1fr;
  gap: 0.5rem;
  align-items: stretch;
}

.pd-card {
  padding: 1.25rem 0.9rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
  align-items: center;
  text-align: center;
}

.pd-num {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  color: var(--vue-green-light);
  opacity: 0.75;
}

.pd-name {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
}

.pd-note {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.6rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.pd-arrow {
  display: flex;
  align-items: center;
  font-family: var(--font-display);
  font-size: 1.2rem;
  color: var(--vue-green);
  padding: 0 0.1rem;
}

.pd-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}

.pd-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
Context lever, stop 2: the spec pipeline architecture — what specs ARE and how they get made.

DELIVERY:
- "Context isn't just files. Some of the most important context is GENERATED — the spec pipeline produces it."
- Point at the dashed research box: "It starts with parallel research. Three subagents go simultaneously — research-lead, integration-researcher, codebase-explorer — fan out, return synthesized findings."
- "Everything below that? One agent runs the pipeline. Discovery → requirements → design → tasks. Same main thread, working through stages. Each artifact narrows the next decision."
- Plant the seed for later: "You'll notice the research happens in parallel — we'll come back to that pattern in the Tools section."
- Land the caption: "Parallel research fans in. One agent runs the pipeline — each artifact narrows the next."

NEXT SLIDE: the vendor-portability beat. Same pipeline exists as a Claude Code plugin AND a pi.dev skill.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="vp-slide">
  <div class="vp-kicker">02 · Context — same pattern, two tools</div>
  <p class="vp-headline">The <span class="vp-em">spec pipeline</span> travels across vendors.</p>
  <div class="vp-cards">
    <div class="vp-card vp-card-claude">
      <div class="vp-platform">Claude Code</div>
      <div class="vp-badge">plugin · 4 agents</div>
      <div class="vp-name">spec-gen</div>
      <div class="vp-agents">
        <div class="vp-agent">research-lead</div>
        <div class="vp-agent">integration-researcher</div>
        <div class="vp-agent">codebase-explorer</div>
        <div class="vp-agent">requirements-analyst</div>
      </div>
      <div class="vp-cap vp-cap-yes">✓ multi-agent orchestration</div>
    </div>
    <div class="vp-card vp-card-pi">
      <div class="vp-platform">pi.dev</div>
      <div class="vp-badge">skill · 1 agent</div>
      <div class="vp-name">spec-gen</div>
      <div class="vp-agents">
        <div class="vp-agent vp-agent-solo">single sequential agent</div>
      </div>
      <div class="vp-cap vp-cap-no">↳ single agent, sequential</div>
    </div>
  </div>
  <p class="vp-caption">Same pipeline. Same artifacts. <span class="vp-em">Multi-agent is a capability — not the pattern.</span></p>
</div>

<style>
.vp-slide {
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.vp-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.vp-headline {
  font-family: var(--font-display);
  font-size: 1.55rem;
  font-weight: 600;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.015em;
}

.vp-em {
  color: var(--vue-green-light);
  font-weight: 700;
}

.vp-cards {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.vp-card {
  padding: 1.05rem 1.25rem 1.1rem;
  border: 1px solid var(--border);
  border-radius: 0.7rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.vp-platform {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.vp-badge {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.6rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.85;
}

.vp-name {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 1.35rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
  margin: 0 0 0.15rem;
}

.vp-agents {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.vp-agent {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.74rem;
  color: var(--text-secondary);
  padding: 0.24rem 0.55rem;
  border: 1px solid var(--border-soft);
  border-radius: 0.3rem;
  background: var(--bg-elev-2);
}

.vp-agent-solo {
  color: var(--text-muted);
  font-style: italic;
}

.vp-cap {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.68rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  margin-top: 0.25rem;
  padding-top: 0.4rem;
  border-top: 1px solid var(--border-soft);
}

.vp-cap-yes { color: var(--vue-green-light); }
.vp-cap-no { color: var(--text-muted); }

.vp-caption {
  font-family: var(--font-display);
  font-size: 1.15rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}
</style>

<!--
Vendor-portability slide. The spec-gen pattern lives in two implementations.

DELIVERY:
- "You just saw the architecture. Now the honest picture across tools."
- "spec-gen lives as a Claude Code plugin — four agents, orchestrated. Research-lead, integration-researcher, codebase-explorer, requirements-analyst."
- "It also lives as a pi.dev skill — same pipeline, same artifacts, one sequential agent. pi.dev doesn't support multi-agent orchestration today."
- Land the caption: "Same pipeline. Same artifacts. Multi-agent is a capability — not the pattern."

WHY THIS MATTERS: protects the talk from being read as a Claude-only argument. The methodology is vendor-portable; multi-agent is a Claude Code-only acceleration. The pattern travels; the capability doesn't.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="ccontract-slide">
  <div class="ccontract-kicker">02 · Context — the spec is the comprehension contract</div>
  <div class="ccontract-diagram">
    <div class="ccontract-input">
      <div class="ccontract-input-label">Plan</div>
      <div class="ccontract-input-action">creates →</div>
    </div>
    <div class="ccontract-spec">
      <div class="ccontract-spec-label">SPEC</div>
      <div class="ccontract-spec-name">the artifact you understand</div>
    </div>
    <div class="ccontract-input">
      <div class="ccontract-input-action">← verifies against</div>
      <div class="ccontract-input-label">Eval</div>
    </div>
  </div>
  <div class="ccontract-implement">
    <div class="ccontract-impl-arrow">↑</div>
    <div class="ccontract-impl-line"><span class="ccontract-impl-key">Implement</span> generates code <span class="ccontract-impl-key">against the spec</span></div>
  </div>
  <p class="ccontract-caption">You comprehend the spec. <span class="ccontract-em">The code, you verify.</span></p>
</div>

<style>
.ccontract-slide {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  align-items: center;
  text-align: center;
}

.ccontract-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.ccontract-diagram {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 1.5rem;
  align-items: center;
  width: 100%;
}

.ccontract-input {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
  align-items: center;
}

.ccontract-input-label {
  font-family: var(--font-display);
  font-size: 1.85rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

.ccontract-input-action {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.ccontract-spec {
  padding: 1.4rem 2rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 40%, var(--border));
  border-radius: 0.85rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 80%, var(--vue-green) 20%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  align-items: center;
  box-shadow:
    0 0 26px color-mix(in srgb, var(--vue-green) 18%, transparent),
    inset 0 1px 0 color-mix(in srgb, white 6%, transparent);
}

.ccontract-spec-label {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  font-weight: 600;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.ccontract-spec-name {
  font-family: var(--font-display);
  font-size: 1.4rem;
  font-weight: 600;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

.ccontract-implement {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.4rem;
}

.ccontract-impl-arrow {
  font-family: var(--font-display);
  font-size: 1.5rem;
  color: var(--vue-green);
  opacity: 0.65;
}

.ccontract-impl-line {
  font-family: var(--font-body);
  font-size: 1.05rem;
  color: var(--text-secondary);
}

.ccontract-impl-key {
  color: var(--vue-green-light);
  font-weight: 600;
}

.ccontract-caption {
  font-family: var(--font-display);
  font-size: 1.4rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0;
}

.ccontract-em {
  color: var(--vue-green-light);
  font-weight: 700;
}
</style>

<!--
S18a · "The spec is the comprehension contract." The key framing of the talk, named explicitly.

DELIVERY:
- "This is the framing that does the most work in the talk."
- "Plan creates the spec — the artifact you understand."
- "Implement generates code against it."
- "Eval verifies the code matches it."
- Land: "You comprehend the spec. The code, you verify."
- Pause. This is the moment that earns the whole rest of the talk.
- This slide returns at the close (S27) as a callback.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="substr-slide">
  <div class="substr-kicker">03 · Memory — three substrates</div>
  <div class="substr-grid">
    <div class="substr-card substr-card-1">
      <div class="substr-tag">.review/</div>
      <div class="substr-name">What changed and why</div>
      <div class="substr-desc">RRL artifacts after every meaningful turn.<br/>Typed, timestamped, risk-classified.</div>
    </div>
    <div class="substr-card substr-card-2">
      <div class="substr-tag">specs/</div>
      <div class="substr-name">What we agreed to</div>
      <div class="substr-desc">Per-phase spec bundles.<br/>Discovery → requirements → design → tasks.</div>
    </div>
    <div class="substr-card substr-card-3">
      <div class="substr-tag">state.json</div>
      <div class="substr-name">Where we are</div>
      <div class="substr-desc">Multi-phase workflow checkpoints.<br/>Progressive-context phase tracking.</div>
    </div>
  </div>
  <p class="substr-caption">Three substrates. <span class="substr-em">Three questions the next agent can answer without you.</span></p>
</div>

<style>
.substr-slide {
  max-width: 80rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.substr-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.substr-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.85rem;
}

.substr-card {
  padding: 1.5rem 1.4rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.substr-card-1 { border-color: color-mix(in srgb, #ffcb6b 28%, var(--border)); }
.substr-card-2 { border-color: color-mix(in srgb, #82aaff 28%, var(--border)); }
.substr-card-3 { border-color: color-mix(in srgb, #c792ea 28%, var(--border)); }

.substr-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 700;
  letter-spacing: 0.04em;
  color: var(--text-muted);
}

.substr-card-1 .substr-tag { color: #ffcb6b; }
.substr-card-2 .substr-tag { color: #82aaff; }
.substr-card-3 .substr-tag { color: #c792ea; }

.substr-name {
  font-family: var(--font-display);
  font-size: 1.5rem;
  font-weight: 700;
  letter-spacing: -0.015em;
  color: var(--text-primary);
  line-height: 1.15;
}

.substr-desc {
  font-family: var(--font-body);
  font-size: 0.96rem;
  color: var(--text-secondary);
  line-height: 1.5;
}

.substr-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0;
}

.substr-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
S18e · "Memory in three substrates." Sets up the Memory section.

DELIVERY:
- "Memory isn't one thing. Three substrates, three questions."
- Walk the three cards: .review/, specs/, state.json.
- The closing line is the point: each substrate answers a question the next agent could ask.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="mem-slide">
  <div class="mem-kicker">03 · Memory — the audit trail</div>

  <div class="mem-grid">
    <div class="mem-tree">
      <div class="mem-bar">.review/</div>
      <div class="mem-list">
        <div class="mem-row"><span class="mem-date">2026-05-15 09:42</span> <span class="tier-impl">IMPLEMENTATION</span></div>
        <div class="mem-row"><span class="mem-date">2026-05-15 11:18</span> <span class="tier-qa">QA</span></div>
        <div class="mem-row"><span class="mem-date">2026-05-15 14:03</span> <span class="tier-spec">SPEC</span></div>
        <div class="mem-row"><span class="mem-date">2026-05-16 10:11</span> <span class="tier-impl">IMPLEMENTATION</span></div>
        <div class="mem-row"><span class="mem-date">2026-05-16 16:27</span> <span class="tier-impl">IMPLEMENTATION</span></div>
        <div class="mem-row"><span class="mem-date">2026-05-17 08:55</span> <span class="tier-spec">SPEC</span></div>
        <div class="mem-row mem-current"><span class="mem-date">2026-05-17 13:40</span> <span class="tier-impl">IMPLEMENTATION</span> ← now</div>
      </div>
    </div>
    <div class="mem-artifact">
      <div class="mem-bar">2026-05-17-13-40-implementation.md</div>
      <div class="mem-code">
        <div class="mem-mline mem-h">---</div>
        <div class="mem-mline">type: IMPLEMENTATION</div>
        <div class="mem-mline">timestamp: 2026-05-17T20:40:00Z</div>
        <div class="mem-mline">risk_level: <span class="mem-risk">MEDIUM</span></div>
        <div class="mem-mline">files_changed: 7</div>
        <div class="mem-mline">decision_count: 3</div>
        <div class="mem-mline">diff_hash: a3f9c124</div>
        <div class="mem-mline mem-h">---</div>
        <div class="mem-spacer"></div>
        <div class="mem-mline mem-h">## 30-Second Summary</div>
        <div class="mem-mline">Added scope-aware scanner...</div>
        <div class="mem-spacer"></div>
        <div class="mem-mline mem-h">## High-Risk Segments</div>
        <div class="mem-mline">⚠️ scanner.ts:142–168</div>
        <div class="mem-mline">   Risk: <span class="mem-risk">LOGIC</span></div>
        <div class="mem-spacer"></div>
        <div class="mem-mline mem-h">## Decision Log</div>
        <div class="mem-mline">DEC-014 [EXPLICIT] ...</div>
      </div>
    </div>
  </div>

  <p class="mem-caption">Every meaningful turn leaves a <span class="mem-em">structured, timestamped, risk-classified</span> artifact.</p>
</div>

<style>
.mem-slide {
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.mem-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.mem-grid {
  display: grid;
  grid-template-columns: 1fr 1.1fr;
  gap: 1.2rem;
  align-items: stretch;
}

.mem-tree, .mem-artifact {
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background: var(--bg-elev-1);
  overflow: hidden;
}

.mem-bar {
  padding: 0.55rem 0.9rem;
  background: var(--bg-elev-2);
  border-bottom: 1px solid var(--border-soft);
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  letter-spacing: 0.06em;
  color: var(--text-primary);
  font-weight: 500;
}

.mem-list, .mem-code {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.72rem;
  line-height: 1.65;
  color: var(--text-secondary);
  padding: 0.85rem 1rem;
  margin: 0;
}

.mem-row, .mem-mline { white-space: pre; }
.mem-current { color: var(--vue-green-light); font-weight: 600; }
.mem-date { color: var(--text-muted); margin-right: 0.6rem; }

.tier-impl { color: #ffcb6b; font-weight: 600; }
.tier-qa { color: #c3e88d; font-weight: 600; }
.tier-spec { color: #82aaff; font-weight: 600; }

.mem-h { color: var(--vue-green-light); font-weight: 600; }
.mem-risk { color: #f78c6c; font-weight: 600; }
.mem-spacer { height: 0.4rem; }

.mem-caption {
  font-family: var(--font-display);
  font-size: 1.15rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}

.mem-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
Memory lever, stop 1: the RRL artifact substrate.

DELIVERY:
- "Memory in this harness has multiple substrates. Let's start with the most useful one."
- "Every meaningful turn — anywhere I run Claude — leaves an artifact in .review/."
- Left: a session-level view of the artifact log accumulating over days.
- Right: the structure of one artifact — frontmatter (type, risk, files, decisions), then the summary, risk segments, decision log.
- "It's a project memory. It's also a code review trail. And it's how my future agents know what changed."
- Tee up the next slide: "And because they're structured, the next agent can search them."
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="search-slide">
  <div class="search-kicker">03 · Memory — searchable</div>

  <p class="search-headline">Specs + reviews are indexed.<br/><span class="search-em">Agentic file search</span> turns history into recall.</p>

  <div class="search-flow">
    <div class="search-block">
      <div class="search-block-label">substrate</div>
      <div class="search-block-name">specs/ · .review/</div>
      <div class="search-block-note">structured, time-stamped, in the repo</div>
    </div>
    <div class="search-arrow">→</div>
    <div class="search-block">
      <div class="search-block-label">index</div>
      <div class="search-block-name">chronological · semantic</div>
      <div class="search-block-note">project history, queryable</div>
    </div>
    <div class="search-arrow">→</div>
    <div class="search-block search-active">
      <div class="search-block-label">retrieval</div>
      <div class="search-block-name">on demand, by the agent</div>
      <div class="search-block-note">load only what's relevant now</div>
    </div>
  </div>

  <p class="search-caption">The agent <span class="search-em">remembers the project</span>, not just the conversation.</p>
</div>

<style>
.search-slide {
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.75rem;
}

.search-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.search-headline {
  font-family: var(--font-display);
  font-size: 1.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.015em;
  line-height: 1.3;
}

.search-em {
  color: var(--vue-green-light);
  font-weight: 700;
}

.search-flow {
  display: grid;
  grid-template-columns: 1fr auto 1fr auto 1fr;
  gap: 0.6rem;
  align-items: stretch;
}

.search-block {
  padding: 1.4rem 1.1rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  text-align: center;
}

.search-block.search-active {
  border-color: color-mix(in srgb, var(--vue-green-light) 35%, var(--border));
  box-shadow: 0 0 18px color-mix(in srgb, var(--vue-green) 18%, transparent);
}

.search-block-label {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.8;
}

.search-block-name {
  font-family: var(--font-display);
  font-size: 1.15rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
}

.search-block-note {
  font-family: var(--font-body);
  font-size: 0.85rem;
  color: var(--text-secondary);
}

.search-arrow {
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-display);
  font-size: 1.4rem;
  color: var(--vue-green);
}

.search-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}
</style>

<!--
Memory lever, stop 2: the searchable layer that sits on top of the artifact substrate.

DELIVERY:
- "Structured artifacts on disk are useful. Searchable structured artifacts are transformative."
- Walk the three blocks: substrate → index → retrieval.
- "The agent doesn't just remember THIS conversation — it remembers the project. When it needs to know what we decided three weeks ago, it searches."
- Land on the caption: "The agent remembers the project, not just the conversation."
- This is one of the more share-worthy ideas in the talk. Pause before moving on.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="fts-slide">
  <div class="fts-kicker">03 · Memory — no vector store. just SQL.</div>
  <div class="fts-code">
    <div class="fts-bar">.harness-visualizer/spec-memory.db</div>
    <div class="fts-body">
      <div class="fts-line fts-comment">-- per-section content, chunked by heading</div>
      <div class="fts-line"><span class="fts-kw">CREATE TABLE</span> <span class="fts-id">chunks</span> (</div>
      <div class="fts-line fts-indent">spec_name, kind, heading, heading_path, content</div>
      <div class="fts-line">);</div>
      <div class="fts-spacer"></div>
      <div class="fts-line fts-comment">-- FTS5 mirror, trigger-synced on every write</div>
      <div class="fts-line"><span class="fts-kw">CREATE VIRTUAL TABLE</span> <span class="fts-id">chunks_fts</span> <span class="fts-kw">USING</span> fts5(...);</div>
      <div class="fts-spacer"></div>
      <div class="fts-line fts-comment">-- agent retrieval, on demand</div>
      <div class="fts-line"><span class="fts-kw">SELECT</span> spec_name <span class="fts-kw">FROM</span> chunks_fts</div>
      <div class="fts-line fts-indent"><span class="fts-kw">WHERE</span> chunks_fts <span class="fts-kw">MATCH</span> <span class="fts-str">&apos;scope-aware AND scanner&apos;</span>;</div>
    </div>
  </div>
  <p class="fts-caption">No vectors. No fine-tune. <span class="fts-em">Structured artifacts and full-text search.</span></p>
</div>

<style>
.fts-slide {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.fts-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.fts-code {
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background: var(--bg-elev-1);
  overflow: hidden;
}

.fts-bar {
  padding: 0.55rem 0.95rem;
  background: var(--bg-elev-2);
  border-bottom: 1px solid var(--border-soft);
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  letter-spacing: 0.04em;
  color: var(--text-primary);
  font-weight: 500;
}

.fts-body {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.92rem;
  line-height: 1.65;
  padding: 1rem 1.15rem;
  color: var(--text-secondary);
}

.fts-line { white-space: pre; }
.fts-indent { padding-left: 1.5em; }
.fts-spacer { height: 0.45rem; }
.fts-kw { color: var(--code-purple); font-weight: 600; }
.fts-id { color: var(--code-blue); font-weight: 600; }
.fts-str { color: var(--code-green); }
.fts-comment { color: var(--text-faint); font-style: italic; }

.fts-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0;
}

.fts-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
S20a · "No vector store. Just SQL." The proof of how agentic memory actually works in this project.

DELIVERY:
- "When I say 'agentic memory' people assume vectors. It isn't. It's SQLite."
- Walk the schema: chunks + chunks_fts trigger-synced.
- "The agent runs SELECT statements. The full-text index is just FTS5."
- Land: "No vectors. No fine-tune. Just structured artifacts and full-text search."
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="tools-slide">
  <div class="tools-kicker">04 · Tools — what the agent can actually do</div>

  <div class="tools-grid">
    <div class="tools-row tools-row-skills">
      <div class="tool-card">
        <div class="tool-badge">SKILL</div>
        <div class="tool-name">playwright-skill</div>
        <div class="tool-desc">Real-browser drive. Snapshot, click, fill, capture console + network. Session memory.</div>
      </div>
      <div class="tool-card">
        <div class="tool-badge">SKILL</div>
        <div class="tool-name">implementation-skill</div>
        <div class="tool-desc">Single-agent execute against a tasks-doc spec.</div>
      </div>
    </div>
    <div class="tools-row tools-row-plugins">
      <div class="tool-card tool-multi">
        <div class="tool-badge">PLUGIN · 4 agents</div>
        <div class="tool-name">spec-gen</div>
        <div class="tool-desc">discovery → requirements → design → tasks. Specs that become both context and memory.</div>
      </div>
      <div class="tool-card tool-multi">
        <div class="tool-badge">PLUGIN · 5 agents</div>
        <div class="tool-name">claude-build</div>
        <div class="tool-desc">Orchestrator + researcher + test-writer + architect-reviewer + implementer.</div>
      </div>
      <div class="tool-card tool-multi">
        <div class="tool-badge">PLUGIN · 5 agents</div>
        <div class="tool-name">claude-qa</div>
        <div class="tool-desc">qa-auditor + test-strategist + test-generator + regression-tracker + mutation-analyst.</div>
      </div>
    </div>
  </div>

  <p class="tools-caption">Each tool was <span class="tools-em">built to fit this project's grain</span>.</p>
</div>

<style>
.tools-slide {
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.tools-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.tools-grid {
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
}

.tools-row {
  display: grid;
  gap: 0.85rem;
}

.tools-row-skills {
  grid-template-columns: 1fr 1fr;
}

.tools-row-plugins {
  grid-template-columns: 1fr 1fr 1fr;
}

.tool-card {
  padding: 1.4rem 1.25rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
}

.tool-card.tool-multi {
  border-color: color-mix(in srgb, var(--vue-green-light) 25%, var(--border));
}

.tool-badge {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.6rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.85;
}

.tool-name {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 1.3rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
}

.tool-desc {
  font-family: var(--font-body);
  font-size: 0.95rem;
  color: var(--text-secondary);
  line-height: 1.45;
}

.tools-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}

.tools-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
Tools lever, stop 1: inventory.

DELIVERY:
- "Tools are what the agent can actually DO inside this project."
- Walk the five cards. Skills first (single-purpose), plugins next (multi-agent orchestrations).
- The closing line is the point: "Each tool was built to fit THIS project's grain." — not off-the-shelf, not generic.
- NEXT: we'll walk Plan → Implement → Validate through spec-gen, claude-build, claude-qa.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="sg-slide">
  <div class="sg-kicker">04 · Tools — <span class="sg-step">Plan</span> · <code>spec-gen</code></div>

  <div class="sg-flow">
    <div class="sg-research">
      <div class="sg-research-tag">PARALLEL RESEARCH · subagents fan out</div>
      <div class="sg-research-chips">
        <span class="sg-chip">research-lead</span>
        <span class="sg-chip">integration-researcher</span>
        <span class="sg-chip">codebase-explorer</span>
        <span class="sg-chip">requirements-analyst</span>
      </div>
    </div>
    <div class="sg-arrow">↓</div>
    <div class="sg-outputs">
      <div class="sg-outputs-tag">THE SPEC BUNDLE</div>
      <div class="sg-outputs-grid">
        <div class="sg-out"><div class="sg-out-name">discovery.md</div><div class="sg-out-desc">scope · constraints · sources</div></div>
        <div class="sg-out"><div class="sg-out-name">research-briefs.md</div><div class="sg-out-desc">synthesized findings</div></div>
        <div class="sg-out"><div class="sg-out-name">requirements.md</div><div class="sg-out-desc">EARS · functional + non-functional</div></div>
        <div class="sg-out"><div class="sg-out-name">design.md</div><div class="sg-out-desc">architecture · diagrams · trade-offs</div></div>
        <div class="sg-out sg-out-final"><div class="sg-out-name">tasks.md</div><div class="sg-out-desc">dependency-ordered implementation surface</div></div>
      </div>
    </div>
  </div>

  <p class="sg-caption">Plan once. <span class="sg-em">Every artifact anchors what comes next.</span></p>
</div>

<style>
.sg-slide {
  max-width: 84rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
}

.sg-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.sg-step {
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 700;
}

.sg-kicker code {
  font-family: var(--font-mono);
  font-size: 0.95em;
}

.sg-flow {
  display: flex;
  flex-direction: column;
  gap: 0.45rem;
  align-items: center;
}

.sg-research {
  width: 100%;
  padding: 0.85rem 1.1rem;
  border: 1px dashed color-mix(in srgb, var(--vue-green-light) 30%, var(--border));
  border-radius: 0.55rem;
  background: color-mix(in srgb, var(--bg-elev-1) 90%, var(--vue-green) 10%);
  display: flex;
  flex-direction: column;
  gap: 0.45rem;
  align-items: center;
}

.sg-research-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.sg-research-chips {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  justify-content: center;
}

.sg-chip {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.72rem;
  font-weight: 500;
  color: var(--text-primary);
  padding: 0.28rem 0.6rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 22%, var(--border));
  border-radius: 0.35rem;
  background: var(--bg-elev-2);
}

.sg-arrow {
  font-family: var(--font-display);
  font-size: 1.4rem;
  color: var(--vue-green);
  opacity: 0.7;
  line-height: 1;
}

.sg-outputs {
  width: 100%;
  padding: 0.85rem 1rem 1rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.sg-outputs-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  text-align: center;
}

.sg-outputs-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 0.5rem;
}

.sg-out {
  padding: 0.55rem 0.65rem;
  border: 1px solid var(--border);
  border-radius: 0.4rem;
  background: var(--bg-elev-2);
  display: flex;
  flex-direction: column;
  gap: 0.18rem;
}

.sg-out-final {
  border-color: color-mix(in srgb, var(--vue-green-light) 40%, var(--border));
  box-shadow: 0 0 14px color-mix(in srgb, var(--vue-green) 14%, transparent);
}

.sg-out-name {
  font-family: var(--font-mono);
  font-size: 0.85rem;
  font-weight: 700;
  color: var(--text-primary);
}

.sg-out-final .sg-out-name {
  color: var(--vue-green-light);
}

.sg-out-desc {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  letter-spacing: 0.03em;
  color: var(--text-muted);
  line-height: 1.35;
}

.sg-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0.2rem 0 0;
  text-align: center;
}

.sg-em {
  color: var(--vue-green-light);
  font-weight: 700;
}
</style>

<!--
04 · Tools — Plan: spec-gen. Opens the P→I→V section.

DELIVERY:
- "Three tools, three steps. Plan, Implement, Validate. Spec-gen is the Plan tool."
- Point at the dashed research band: "Multi-agent — parallel research at the front. Four subagents fan out, return synthesized findings. (We'll come back to multi-agent in a couple slides.)"
- Point at the output grid: "Out the other end: a spec bundle. Five artifacts. Discovery, research, requirements in EARS format, design with diagrams, tasks in dependency order."
- Highlight tasks.md (the green-glowing card): "Tasks.md is the implementation surface — the handoff to the next step."
- Land the caption: "Plan once. Every artifact anchors what comes next."

WHY THIS LANDS: anchors P→I→V on a concrete output the audience can picture, and primes them to think of the next slide (claude-build) as consuming this output.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="cb-slide">
  <div class="cb-kicker">04 · Tools — <span class="sg-step">Implement</span> · <code>claude-build</code></div>

  <div class="cb-waves">
    <div class="cb-wave">
      <div class="cb-wave-tag">WAVE 0</div>
      <div class="cb-wave-name">contracts</div>
      <div class="cb-wave-roles">
        <div class="cb-role cb-role-imp">1× implementer</div>
      </div>
      <div class="cb-wave-note">sets types &amp; interfaces &mdash; nothing else moves yet</div>
    </div>
    <div class="cb-wave-arrow">→</div>
    <div class="cb-wave cb-wave-mid">
      <div class="cb-wave-tag">WAVE 1</div>
      <div class="cb-wave-name">parallel build</div>
      <div class="cb-wave-roles">
        <div class="cb-role cb-role-imp">3× implementers</div>
      </div>
      <div class="cb-wave-note">work in parallel &mdash; no file collisions, contracts hold</div>
    </div>
    <div class="cb-wave-arrow">→</div>
    <div class="cb-wave">
      <div class="cb-wave-tag">WAVE 2</div>
      <div class="cb-wave-name">integration</div>
      <div class="cb-wave-roles">
        <div class="cb-role cb-role-imp">1× implementer</div>
        <div class="cb-role cb-role-arch">architect-reviewer</div>
        <div class="cb-role cb-role-test">test-writer</div>
      </div>
      <div class="cb-wave-note">stitch, review, write tests</div>
    </div>
  </div>

  <div class="cb-side">
    <span class="cb-side-tag">across all waves</span>
    <span class="cb-side-chip"><code>implementation-orchestrator</code> &middot; coordinates</span>
    <span class="cb-side-chip"><code>researcher</code> &middot; on-demand lookups</span>
  </div>

  <p class="cb-caption"><span class="cb-em">Wave 0 sets the contracts.</span> Wave 1 can&rsquo;t collide. Wave 2 verifies.</p>
</div>

<style>
.cb-slide {
  max-width: 82rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.9rem;
}

.cb-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.cb-kicker code {
  font-family: var(--font-mono);
  font-size: 0.95em;
}

.cb-waves {
  display: grid;
  grid-template-columns: 1fr auto 1fr auto 1fr;
  gap: 0.5rem;
  align-items: stretch;
}

.cb-wave {
  padding: 1rem 1.1rem;
  border: 1px solid var(--border);
  border-radius: 0.65rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.45rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.cb-wave-mid {
  border-color: color-mix(in srgb, var(--vue-green-light) 38%, var(--border));
  box-shadow:
    inset 0 1px 0 color-mix(in srgb, white 5%, transparent),
    0 0 18px color-mix(in srgb, var(--vue-green) 16%, transparent);
}

.cb-wave-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  color: var(--vue-green-light);
}

.cb-wave-name {
  font-family: var(--font-display);
  font-size: 1.35rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
  line-height: 1.1;
}

.cb-wave-roles {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  margin-top: 0.15rem;
}

.cb-role {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  padding: 0.28rem 0.55rem;
  border: 1px solid var(--border-soft);
  border-radius: 0.3rem;
  background: var(--bg-elev-2);
  color: var(--text-secondary);
}

.cb-role-imp { color: #ffcb6b; border-color: color-mix(in srgb, #ffcb6b 22%, var(--border)); }
.cb-role-arch { color: #82aaff; border-color: color-mix(in srgb, #82aaff 22%, var(--border)); }
.cb-role-test { color: #c3e88d; border-color: color-mix(in srgb, #c3e88d 22%, var(--border)); }

.cb-wave-note {
  font-family: var(--font-body);
  font-size: 0.85rem;
  color: var(--text-secondary);
  line-height: 1.4;
  margin-top: auto;
  padding-top: 0.3rem;
}

.cb-wave-arrow {
  display: flex;
  align-items: center;
  font-family: var(--font-display);
  font-size: 1.3rem;
  color: var(--vue-green);
  opacity: 0.6;
}

.cb-side {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 0.5rem 1rem;
  padding: 0.5rem 0.9rem;
  border: 1px dashed color-mix(in srgb, var(--vue-green-light) 26%, var(--border));
  border-radius: 0.5rem;
  background: var(--bg-elev-1);
}

.cb-side-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.cb-side-chip {
  font-family: var(--font-body);
  font-size: 0.82rem;
  color: var(--text-secondary);
  white-space: nowrap;
}

.cb-side-chip code {
  font-family: var(--font-mono);
  font-size: 0.88em;
}

.cb-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0.2rem 0 0;
  text-align: center;
}

.cb-em {
  color: var(--vue-green-light);
  font-weight: 700;
}
</style>

<!--
04 · Tools — claude-build deep dive. Five agents, three waves.

DELIVERY:
- "Multi-agent for IMPLEMENTATION. Five roles, three waves."
- Walk Wave 0: "One implementer. Sets the contracts — types, interfaces, module boundaries. Everyone else waits."
- Walk Wave 1: "Three implementers in parallel. They CAN'T collide because Wave 0 already drew the lines."
- Walk Wave 2: "One implementer stitches it together. Architect-reviewer reads the diff against design intent. Test-writer covers the new surface."
- Point at the dashed side band: "Orchestrator coordinates the whole thing. Researcher is on-demand."
- Land the caption: "Wave 0 sets the contracts. Wave 1 can't collide. Wave 2 verifies."

CROSS-VENDOR NOTE (speak, don't slide): "pi.dev users get the same idea with implementation-skill — single agent, sequential, same artifacts. Same JOB, different tool. The harness travels."

WHY THIS LANDS: the wave pattern is the most memorable, teachable detail in the whole talk. Audience leaves knowing what "contracts-first parallelism" looks like.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="qa-slide">
  <div class="qa-kicker">04 · Tools — <span class="sg-step">Validate</span> · <code>claude-qa</code></div>

  <div class="qa-grid">
    <div class="qa-row qa-row-top">
      <div class="qa-card">
        <div class="qa-card-tag">ANALYZE</div>
        <div class="qa-card-name">test-strategist</div>
        <div class="qa-card-desc">Risks + priorities. What surface needs covered next.</div>
      </div>
      <div class="qa-card">
        <div class="qa-card-tag">GENERATE</div>
        <div class="qa-card-name">test-generator</div>
        <div class="qa-card-desc">Writes Vitest coverage based on strategist&rsquo;s risk map.</div>
      </div>
      <div class="qa-card">
        <div class="qa-card-tag">AUDIT</div>
        <div class="qa-card-name">qa-auditor</div>
        <div class="qa-card-desc">Reviews against architectural best practices and spec design.</div>
      </div>
    </div>
    <div class="qa-row qa-row-bottom">
      <div class="qa-card qa-card-time">
        <div class="qa-card-tag">TRACK</div>
        <div class="qa-card-name">regression-tracker</div>
        <div class="qa-card-desc">Quality metrics over time. Trends, not snapshots.</div>
      </div>
      <div class="qa-card qa-card-time">
        <div class="qa-card-tag">GAPS</div>
        <div class="qa-card-name">mutation-analyst</div>
        <div class="qa-card-desc">Where the tests didn&rsquo;t catch a real change.</div>
      </div>
    </div>
  </div>

  <div class="qa-spec">
    <span class="qa-spec-tag">when a spec is in scope · the loop closes</span>
    <span class="qa-spec-body"><code>qa-auditor</code> verifies the implementation against <code>design.md</code>, every <em>must-have</em> requirement is exercised, and tests trace back to the requirements that demanded them.</span>
  </div>

  <p class="qa-caption">Specialized roles, parallel verification &mdash; <span class="qa-em">anchored to the spec</span>.</p>
</div>

<style>
.qa-slide {
  max-width: 82rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.9rem;
}

.qa-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.qa-kicker code {
  font-family: var(--font-mono);
  font-size: 0.95em;
}

.qa-grid {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.qa-row {
  display: grid;
  gap: 0.6rem;
}

.qa-row-top {
  grid-template-columns: 1fr 1fr 1fr;
}

.qa-row-bottom {
  grid-template-columns: 1fr 1fr;
  max-width: 56rem;
  margin: 0 auto;
  width: 100%;
}

.qa-card {
  padding: 0.95rem 1.1rem 1rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.qa-card-time {
  border-color: color-mix(in srgb, #c792ea 22%, var(--border));
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, #c792ea 8%) 0%,
      var(--bg-elev-1) 100%);
}

.qa-card-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.6rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.qa-card-time .qa-card-tag {
  color: #c792ea;
}

.qa-card-name {
  font-family: var(--font-mono);
  font-size: 1.15rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
}

.qa-card-desc {
  font-family: var(--font-body);
  font-size: 0.88rem;
  color: var(--text-secondary);
  line-height: 1.45;
}

.qa-spec {
  margin-top: 0.2rem;
  padding: 0.7rem 1.1rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 38%, var(--border));
  border-radius: 0.55rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 82%, var(--vue-green) 18%) 0%,
      var(--bg-elev-1) 100%);
  box-shadow:
    inset 0 1px 0 color-mix(in srgb, white 5%, transparent),
    0 0 22px color-mix(in srgb, var(--vue-green) 14%, transparent);
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  text-align: center;
}

.qa-spec-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.65rem;
  font-weight: 600;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.qa-spec-body {
  font-family: var(--font-body);
  font-size: 0.95rem;
  color: var(--text-primary);
  line-height: 1.5;
}

.qa-spec-body code {
  font-family: var(--font-mono);
  font-size: 0.88em;
}

.qa-spec-body em {
  color: var(--vue-green-light);
  font-style: italic;
  font-weight: 600;
}

.qa-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0.2rem 0 0;
  text-align: center;
}

.qa-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 700;
}
</style>

<!--
04 · Tools — claude-qa deep dive. Five specialized auditors, anchored to the spec.

DELIVERY:
- "Multi-agent for QA. Five specialized roles, each owns a slice of verification."
- Top row, left to right: "Strategist maps risk. Generator writes the tests. Auditor checks architecture against the design."
- Bottom row (purple-tinted, the time dimension): "Regression-tracker watches quality across runs. Mutation-analyst finds where the tests are theater — code changed, no test caught it."
- Point at the GREEN spec-aware band: "And this is the loop closing. When a spec is in scope, the qa-auditor doesn't just review architecture — it verifies the implementation against design.md. Every must-have requirement gets exercised. Every test traces back to a requirement that demanded it."
- Land the caption: "Specialized roles, parallel verification — anchored to the spec."

CALLBACK: this is the operational answer to S18a — "the spec is the comprehension contract." Here's where the contract actually gets checked.

PAIRING NOTE: this completes the multi-agent picture across the harness. spec-gen for PLAN, claude-build for IMPLEMENT, claude-qa for VALIDATE. Three plugins, one shape — orchestrator coordinates specialists, and when there's a spec, the verification anchors back to it.

NEXT: now that the audience has seen multi-agent in THREE places (spec-gen research, claude-build waves, claude-qa auditors), we land the orchestration GO/STAY rubric. Concrete before abstract.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="moa-slide moa-slide-single">
  <div class="moa-kicker">Orchestration · go multi-agent when&hellip;</div>

  <div class="moa-col moa-go moa-col-wide">
    <ul class="moa-list">
      <li><span class="moa-rule">Independent lanes</span><span class="moa-note">no shared files, clean boundaries</span></li>
      <li><span class="moa-rule">Coverage beats depth</span><span class="moa-note">many shallow passes — research, tests, audits</span></li>
      <li><span class="moa-rule">You&rsquo;re the bottleneck</span><span class="moa-note">delegate, then review</span></li>
      <li><span class="moa-rule">Interfaces are already clear</span><span class="moa-note">contracts let agents work without colliding</span></li>
    </ul>
  </div>

  <div class="moa-proof">
    <span class="moa-proof-label">you just saw this in</span>
    <span class="moa-proof-chip"><code>spec-gen</code> · research fans out</span>
    <span class="moa-proof-chip"><code>claude-build</code> · implementer waves</span>
    <span class="moa-proof-chip"><code>claude-qa</code> · parallel audit</span>
  </div>
</div>

<!--
Orchestration · GO heuristic. After the audience has seen multi-agent in three plugins.

DELIVERY:
- "You've just seen multi-agent in three places. Here's the rubric — when does it earn its keep?"
- Walk the four green criteria: independent lanes, coverage beats depth, you're the bottleneck, interfaces are clear.
- Point at the dashed proof band: "All four fire in spec-gen's research, claude-build's waves, claude-qa's auditors. That's why those got multi-agent."
- 30–45 seconds. Tee up the inverse on the next slide.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="moa-slide moa-slide-single">
  <div class="moa-kicker">Orchestration · stay single-agent when&hellip;</div>

  <div class="moa-col moa-stay moa-col-wide">
    <ul class="moa-list">
      <li><span class="moa-rule">The work is sequential</span><span class="moa-note">each step depends on the last</span></li>
      <li><span class="moa-rule">You&rsquo;re still shaping the problem</span><span class="moa-note">vague reqs, exploration, design talk</span></li>
      <li><span class="moa-rule">It&rsquo;s a small, local change</span><span class="moa-note">one PR&rsquo;s worth — overhead won&rsquo;t pay off</span></li>
      <li><span class="moa-rule">Needs creative coherence</span><span class="moa-note">one mind, end-to-end</span></li>
    </ul>
  </div>

  <p class="moa-caption">When in doubt, <span class="moa-em">start single</span>. Add agents when the bottleneck moves to you.</p>
</div>

<!--
Orchestration · STAY heuristic. Second half of the rubric.

DELIVERY:
- "And when does one agent win?"
- Walk the four amber criteria: sequential, shaping the problem, small/local, creative coherence.
- Land the caption SLOWLY: "When in doubt, start single. Add agents when the bottleneck moves to you."
- 30–45 seconds. This is the takeaway. Pause before moving on.

WHY THE SPLIT: the rubric is more usable when each side has room to breathe. Audience leaves with a portable heuristic.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="pw-slide">
  <div class="pw-kicker">04 · Tools — a worked example</div>
  <div class="pw-grid">
    <div class="pw-summary">
      <div class="pw-title">playwright-skill</div>
      <div class="pw-desc">A custom QA tool for an agent to drive a real browser, capture diagnostics, and report compactly.</div>
      <div class="pw-stats">
        <div class="pw-stat">
          <div class="pw-stat-num">10</div>
          <div class="pw-stat-lbl">bin scripts</div>
        </div>
        <div class="pw-stat">
          <div class="pw-stat-num">200&nbsp;tok</div>
          <div class="pw-stat-lbl">per response</div>
        </div>
        <div class="pw-stat">
          <div class="pw-stat-num">LRU&nbsp;20</div>
          <div class="pw-stat-lbl">cached contexts</div>
        </div>
      </div>
    </div>
    <div class="pw-files">
      <div class="pw-bar">bin/</div>
      <div class="pw-list">
        <div class="pw-row"><span class="pw-name">open</span><span class="pw-note">named session lifecycle</span></div>
        <div class="pw-row"><span class="pw-name">context</span><span class="pw-note">capture full page state</span></div>
        <div class="pw-row"><span class="pw-name">inject-capture</span><span class="pw-note">patch console + fetch</span></div>
        <div class="pw-row"><span class="pw-name">cache-query</span><span class="pw-note">retrieve by data type</span></div>
        <div class="pw-row"><span class="pw-name">click-css</span><span class="pw-note">CSS selector fallback</span></div>
        <div class="pw-row"><span class="pw-name">auth-save</span><span class="pw-note">named auth profiles</span></div>
      </div>
    </div>
  </div>
  <p class="pw-caption">The agent gets a <span class="pw-em">200-token summary</span>. The full context stays in the cache, retrieved only when needed.</p>
</div>

<style>
.pw-slide {
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.pw-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.pw-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  align-items: stretch;
}

.pw-summary {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  padding-top: 0.25rem;
}

.pw-title {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 1.65rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
}

.pw-desc {
  font-family: var(--font-body);
  font-size: 1.05rem;
  color: var(--text-secondary);
  line-height: 1.5;
}

.pw-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.6rem;
  margin-top: 0.5rem;
}

.pw-stat {
  border: 1px solid var(--border);
  border-radius: 0.5rem;
  padding: 0.75rem 0.6rem;
  background: var(--bg-elev-1);
  text-align: center;
}

.pw-stat-num {
  font-family: var(--font-display);
  font-size: 1.45rem;
  font-weight: 700;
  color: var(--vue-green-light);
  letter-spacing: -0.01em;
}

.pw-stat-lbl {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.58rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--text-muted);
  margin-top: 0.15rem;
}

.pw-files {
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background: var(--bg-elev-1);
  overflow: hidden;
}

.pw-bar {
  padding: 0.55rem 0.9rem;
  background: var(--bg-elev-2);
  border-bottom: 1px solid var(--border-soft);
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  letter-spacing: 0.06em;
  color: var(--text-primary);
  font-weight: 500;
}

.pw-list {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  line-height: 1.7;
  padding: 0.85rem 1rem;
  margin: 0;
  color: var(--text-secondary);
}

.pw-row { display: flex; align-items: baseline; gap: 1rem; white-space: nowrap; }
.pw-name { color: var(--vue-green-light); font-weight: 600; min-width: 7.5rem; }
.pw-note { color: var(--text-muted); }

.pw-caption {
  font-family: var(--font-display);
  font-size: 1.15rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}

.pw-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
Tools lever, stop 2: Playwright skill as a worked example of what "build a tool that fits your project" looks like.

DELIVERY:
- "Let's look at one of these in detail. The playwright-skill is a custom QA tool I built for this project."
- "Ten bin scripts — `open`, `context`, `inject-capture`, `cache-query`, and so on."
- Point at the stats: "Every response is about 200 tokens. The full page state is in a cache the agent retrieves only when it needs to."
- The land: "The agent gets a summary. The detail is one command away."
- This is the pattern: tools should compress for the agent and expand on demand. That's where the engineering happens.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="pattern-slide">
  <div class="pattern-kicker">04 · Tools — the transferable pattern</div>
  <div class="pattern-flow">
    <div class="pattern-node pattern-agent">
      <div class="pattern-node-label">agent</div>
      <div class="pattern-node-desc">sees only a summary</div>
    </div>
    <div class="pattern-arrow pattern-arrow-r">→ call</div>
    <div class="pattern-node pattern-skill">
      <div class="pattern-node-label">skill</div>
      <div class="pattern-node-desc">200-token summary</div>
    </div>
    <div class="pattern-arrow pattern-arrow-l">stores</div>
    <div class="pattern-node pattern-cache">
      <div class="pattern-node-label">cache</div>
      <div class="pattern-node-desc">full state on disk</div>
    </div>
  </div>
  <div class="pattern-callout">
    <div class="pattern-callout-arrow">↑</div>
    <div class="pattern-callout-text"><span class="pattern-callout-key">query by name</span>, on demand</div>
  </div>
  <p class="pattern-caption">Compress for the agent. <span class="pattern-em">Expand on demand.</span></p>
</div>

<style>
.pattern-slide {
  max-width: 80rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.4rem;
}

.pattern-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.pattern-flow {
  display: grid;
  grid-template-columns: 1fr auto 1fr auto 1fr;
  gap: 0.85rem;
  align-items: stretch;
}

.pattern-node {
  padding: 1.35rem 1.1rem;
  border: 1px solid var(--border);
  border-radius: 0.65rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
  align-items: center;
  text-align: center;
}

.pattern-skill {
  border-color: color-mix(in srgb, var(--vue-green-light) 40%, var(--border));
  box-shadow: 0 0 18px color-mix(in srgb, var(--vue-green) 14%, transparent);
}

.pattern-node-label {
  font-family: var(--font-display);
  font-size: 1.55rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

.pattern-skill .pattern-node-label { color: var(--vue-green-light); }

.pattern-node-desc {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.72rem;
  letter-spacing: 0.05em;
  color: var(--text-muted);
}

.pattern-arrow {
  display: flex;
  align-items: center;
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.72rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--vue-green);
  padding: 0 0.5rem;
}

.pattern-callout {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
}

.pattern-callout-arrow {
  font-family: var(--font-display);
  font-size: 1.4rem;
  color: var(--vue-green);
  opacity: 0.7;
}

.pattern-callout-text {
  font-family: var(--font-body);
  font-size: 1rem;
  color: var(--text-secondary);
}

.pattern-callout-key {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  color: var(--vue-green-light);
  font-weight: 600;
}

.pattern-caption {
  font-family: var(--font-display);
  font-size: 1.3rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0;
}

.pattern-em {
  color: var(--vue-green-light);
  font-weight: 700;
}
</style>

<!--
S22a · "The transferable pattern: compress, then expand on demand."

DELIVERY:
- "Every custom skill I build follows this shape."
- Walk the flow: agent → skill (summary) ← stores → cache.
- "The agent gets a short summary. The full state stays in a cache, queryable by name."
- Land: "Compress for the agent. Expand on demand. That's how you build tools that don't blow the context window."
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="hooks-slide">
  <div class="hooks-kicker">04 · Tools — hooks, the automatic harness</div>
  <div class="hooks-code">
    <div class="hooks-bar">.claude/settings.json</div>
    <div class="hooks-body">
      <div class="hooks-line">{</div>
      <div class="hooks-line">&nbsp;&nbsp;<span class="hooks-key">&quot;hooks&quot;</span>: {</div>
      <div class="hooks-line">&nbsp;&nbsp;&nbsp;&nbsp;<span class="hooks-key">&quot;PostToolUse&quot;</span>: [<span class="hooks-str">&quot;rapid-review&quot;</span>],</div>
      <div class="hooks-line">&nbsp;&nbsp;&nbsp;&nbsp;<span class="hooks-key">&quot;Stop&quot;</span>:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[<span class="hooks-str">&quot;rapid-review-mark&quot;</span>]</div>
      <div class="hooks-line">&nbsp;&nbsp;}</div>
      <div class="hooks-line">}</div>
    </div>
  </div>
  <div class="hooks-effects">
    <div class="hooks-effect">
      <div class="hooks-effect-when">every tool call</div>
      <div class="hooks-effect-arrow">→</div>
      <div class="hooks-effect-what">artifact in <code>.review/</code></div>
    </div>
    <div class="hooks-effect">
      <div class="hooks-effect-when">every session-end</div>
      <div class="hooks-effect-arrow">→</div>
      <div class="hooks-effect-what">commit-ready marker</div>
    </div>
  </div>
  <p class="hooks-caption">Hooks make the harness write its own audit trail. <span class="hooks-em">I don&rsquo;t have to remember.</span></p>
</div>

<style>
.hooks-slide {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.hooks-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.hooks-code {
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background: var(--bg-elev-1);
  overflow: hidden;
}

.hooks-bar {
  padding: 0.55rem 0.95rem;
  background: var(--bg-elev-2);
  border-bottom: 1px solid var(--border-soft);
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  letter-spacing: 0.04em;
  color: var(--text-primary);
  font-weight: 500;
}

.hooks-body {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.95rem;
  line-height: 1.7;
  padding: 1rem 1.15rem;
  color: var(--text-secondary);
}

.hooks-line { white-space: pre; }
.hooks-key { color: var(--code-blue); }
.hooks-str { color: var(--code-green); }

.hooks-effects {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.75rem;
}

.hooks-effect {
  padding: 0.85rem 1.1rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 22%, var(--border));
  border-radius: 0.5rem;
  background: var(--bg-elev-1);
  display: grid;
  grid-template-columns: auto auto 1fr;
  align-items: center;
  gap: 0.85rem;
}

.hooks-effect-when {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.72rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.hooks-effect-arrow {
  color: var(--vue-green);
  opacity: 0.65;
}

.hooks-effect-what {
  font-family: var(--font-body);
  font-size: 1rem;
  color: var(--text-primary);
}

.hooks-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0;
}

.hooks-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
S22d · "Hooks — the automatic harness."

DELIVERY:
- "Hooks are how the harness writes its own audit trail."
- "Every tool call generates a review artifact. Every session-end marks it ready to commit."
- "I don't have to remember; the harness remembers for me."
- NOTE: package the actual hook scripts into harness-visualizer before the talk so the audience can grab them.
-->


---
layout: default
class: '!justify-center'
transition: fade
---

<div class="risk-slide">
  <div class="risk-kicker">05 · Evaluation — read closely, where it matters</div>

  <p class="risk-headline">Not all AI-generated code deserves equal attention.</p>

  <div class="risk-grid">
    <div class="risk-card risk-1">
      <div class="risk-tag">01 · LOW</div>
      <div class="risk-name">Boilerplate</div>
      <div class="risk-ex">DTOs · getters · fixtures · scaffolding</div>
    </div>
    <div class="risk-card risk-2">
      <div class="risk-tag">02 · MED</div>
      <div class="risk-name">Logic</div>
      <div class="risk-ex">business rules · conditionals · transformations</div>
    </div>
    <div class="risk-card risk-3">
      <div class="risk-tag">03 · HIGH</div>
      <div class="risk-name">Blast radius</div>
      <div class="risk-ex">auth · credentials · external APIs · payments</div>
    </div>
    <div class="risk-card risk-4">
      <div class="risk-tag">04 · CRIT</div>
      <div class="risk-name">Irreversible</div>
      <div class="risk-ex">DROP/TRUNCATE · destructive migrations · infra</div>
    </div>
  </div>

  <p class="risk-caption">Take this home. <span class="risk-em">It's the entire frame for what you read carefully.</span></p>
</div>

<style>
.risk-slide {
  max-width: 74rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.risk-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.risk-headline {
  font-family: var(--font-display);
  font-size: 2rem;
  font-weight: 600;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.015em;
}

.risk-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0.7rem;
}

.risk-card {
  padding: 1.4rem 1rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background: var(--bg-elev-1);
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  text-align: left;
}

.risk-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.6rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}

.risk-1 { border-color: color-mix(in srgb, #c3e88d 30%, var(--border)); }
.risk-1 .risk-tag { color: #c3e88d; }
.risk-1 .risk-name { color: #c3e88d; }

.risk-2 { border-color: color-mix(in srgb, #ffcb6b 30%, var(--border)); }
.risk-2 .risk-tag { color: #ffcb6b; }
.risk-2 .risk-name { color: #ffcb6b; }

.risk-3 { border-color: color-mix(in srgb, #f78c6c 35%, var(--border)); }
.risk-3 .risk-tag { color: #f78c6c; }
.risk-3 .risk-name { color: #f78c6c; }

.risk-4 {
  border-color: color-mix(in srgb, #f07178 40%, var(--border));
  box-shadow: 0 0 14px color-mix(in srgb, #f07178 15%, transparent);
}
.risk-4 .risk-tag { color: #f07178; }
.risk-4 .risk-name { color: #f07178; }

.risk-name {
  font-family: var(--font-display);
  font-size: 1.45rem;
  font-weight: 700;
  letter-spacing: -0.015em;
}

.risk-ex {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.04em;
  color: var(--text-muted);
  line-height: 1.5;
}

.risk-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
}

.risk-em {
  color: var(--vue-green-light);
  font-weight: 600;
}
</style>

<!--
Evaluation lever, stop 2: the risk taxonomy. THE AUDIENCE TAKEAWAY of the section.

DELIVERY:
- "If you take one thing home from this talk, take this."
- Walk the four cards from low to critical. Read the examples on each.
- "BOILERPLATE — scan, sign off. LOGIC — read, but trust your tests. BLAST RADIUS — read every line. IRREVERSIBLE — read every line twice, and re-read after the agent runs."
- "This is the frame the architect-reviewer subagent uses. This is the frame I use. This is the frame your reviewers should use."
- Pause. Then transition to the demo.

NEXT SLIDE: live cross-vendor demo setup.
-->

---
layout: default
class: '!justify-center text-center'
transition: fade
---

<div class="live-tee-slide">
  <div class="live-kicker">now we drive it live</div>
  <div class="live-rows">
    <div class="live-row">
      <div class="live-row-num">01</div>
      <div class="live-row-stack">
        <div class="live-row-line"><span class="live-agent">Claude Code</span><span class="live-sep">·</span><span class="live-model">Opus 4.7</span></div>
        <div class="live-row-line live-row-mid"><span class="live-plus">+</span><span class="live-skill">playwright-skill</span></div>
        <div class="live-row-line live-row-action"><span class="live-arrow">→</span> drives the visualizer</div>
      </div>
    </div>
    <div class="live-row">
      <div class="live-row-num">02</div>
      <div class="live-row-stack">
        <div class="live-row-line"><span class="live-agent">pi.dev</span><span class="live-sep">·</span><span class="live-model">GPT-5.5</span></div>
        <div class="live-row-line live-row-mid"><span class="live-plus">+</span><span class="live-skill">playwright-skill</span></div>
        <div class="live-row-line live-row-action"><span class="live-arrow">→</span> drives the visualizer</div>
      </div>
    </div>
  </div>
  <p class="live-caption"><span class="live-em">Same skill.</span> Two runtimes.</p>
</div>

<style>
.live-tee-slide {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.live-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.live-rows {
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
}

.live-row {
  padding: 1.5rem 1.75rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 30%, var(--border));
  border-radius: 0.75rem;
  background:
    linear-gradient(110deg,
      color-mix(in srgb, var(--bg-elev-1) 86%, var(--vue-green) 14%) 0%,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-blue) 8%) 100%);
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 1.5rem;
  align-items: center;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 5%, transparent);
}

.live-row-num {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 1.2rem;
  font-weight: 700;
  letter-spacing: 0.1em;
  color: var(--vue-green-light);
  padding: 0.4rem 0.75rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 35%, var(--border));
  border-radius: 0.4rem;
  background: var(--bg-elev-2);
}

.live-row-stack {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.live-row-line {
  display: flex;
  align-items: center;
  gap: 0.6rem;
}

.live-agent {
  font-family: var(--font-display);
  font-size: 1.6rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

.live-sep {
  color: var(--text-faint);
}

.live-model {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  letter-spacing: 0.06em;
  color: var(--text-muted);
}

.live-plus {
  font-family: var(--font-display);
  font-size: 1.5rem;
  color: var(--vue-green);
  font-weight: 300;
}

.live-skill {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 1rem;
  font-weight: 600;
  color: var(--code-cyan);
  padding: 0.2em 0.6em;
  background: var(--bg-elev-2);
  border: 1px solid color-mix(in srgb, var(--code-cyan) 22%, var(--border));
  border-radius: 0.35em;
}

.live-arrow {
  font-family: var(--font-display);
  font-size: 1.5rem;
  color: var(--vue-green);
  opacity: 0.7;
}

.live-row-action {
  font-family: var(--font-display);
  font-size: 1.2rem;
  color: var(--text-secondary);
  font-style: italic;
}

.live-caption {
  font-family: var(--font-display);
  font-size: 1.4rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0;
  text-align: center;
}

.live-em {
  color: var(--vue-green-light);
  font-weight: 700;
}
</style>

<!--
S25 · Live cross-vendor demo setup card. REPLACES the old "Plan → Implement → Validate" tee.

DELIVERY:
- "I'm going to spin up the app. First with Claude Code, driving with the playwright-skill."
- "Then I'll switch to pi.dev — GPT-5.5 — same skill, drive a different part."
- "Same skill, two runtimes. Watch what travels and what doesn't."

NEXT: live moment 1 (Claude Code drives the visualizer — accordion, tabs, table view).
-->

---
layout: default
class: '!justify-center text-center'
transition: fade
---

<div class="switch-slide">
  <div class="switch-kicker">switching runtimes</div>
  <h1 class="switch-line">
    <span class="switch-from">Claude Code</span>
    <span class="switch-arrow">→</span>
    <span class="switch-to">pi.dev <span class="switch-model">· GPT-5.5</span></span>
  </h1>
  <p class="switch-sub">Same <span class="switch-em">playwright-skill</span>. Different agent.</p>
</div>

<style>
.switch-slide {
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.switch-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.switch-line {
  font-family: var(--font-display) !important;
  font-size: 3.4rem !important;
  font-weight: 700 !important;
  margin: 0 !important;
  display: flex;
  align-items: baseline;
  gap: 1.5rem;
  letter-spacing: -0.02em;
  line-height: 1.1 !important;
}

.switch-from {
  color: var(--text-muted);
  font-weight: 600;
}

.switch-to {
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.switch-model {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 1.4rem;
  font-weight: 500;
  color: var(--text-muted);
  -webkit-text-fill-color: var(--text-muted);
  letter-spacing: 0.06em;
}

.switch-arrow {
  color: var(--vue-green);
  opacity: 0.6;
  font-weight: 400;
  font-size: 2.5rem;
}

.switch-sub {
  font-family: var(--font-body);
  font-size: 1.25rem;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}

.switch-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
S25b · Runtime switch transition card. Shown between live moment 1 (Claude Code) and live moment 2 (pi.dev).

DELIVERY:
- "Same skill. Different agent."
- Don't read more. Switch to the running app. Demo pi.dev with the same playwright-skill.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="recap-slide">
  <div class="recap-kicker">what you just saw</div>
  <div class="recap-rows">
    <div class="recap-row">
      <div class="recap-agent">Claude Code</div>
      <div class="recap-sep"></div>
      <div class="recap-action">browse · accordion · tabs · table</div>
    </div>
    <div class="recap-row">
      <div class="recap-agent">pi.dev</div>
      <div class="recap-sep"></div>
      <div class="recap-action">open · edit markdown · save · re-render</div>
    </div>
  </div>
  <p class="recap-caption">Two vendors. One harness. <span class="recap-em">Same skill, written once.</span></p>
</div>

<style>
.recap-slide {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.recap-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.recap-rows {
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
}

.recap-row {
  display: grid;
  grid-template-columns: 12rem 1px 1fr;
  gap: 1.5rem;
  align-items: center;
  padding: 1.25rem 1.5rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background: var(--bg-elev-1);
}

.recap-agent {
  font-family: var(--font-display);
  font-size: 1.55rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

.recap-sep {
  width: 1px;
  height: 70%;
  background: var(--border);
}

.recap-action {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 1rem;
  color: var(--vue-green-light);
  letter-spacing: 0.04em;
}

.recap-caption {
  font-family: var(--font-display);
  font-size: 1.3rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}

.recap-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
S25c · Live demo recap. Lands the cross-vendor proof.

DELIVERY:
- "Two agents. One custom tool I wrote once."
- Beat. "That's what vendor-portability buys you."
- Then transition into the close.
-->

---
layout: default
class: '!justify-center text-center'
transition: fade
---

<div class="close-1-slide">
  <p class="close-line-1">You didn&rsquo;t read every line.</p>
  <p class="close-line-2">You also didn&rsquo;t ship dark code.</p>
  <p class="close-cap">That&rsquo;s the dichotomy escape.</p>
</div>

<style>
.close-1-slide {
  max-width: 70rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.close-line-1 {
  font-family: var(--font-display);
  font-size: 3.4rem;
  font-weight: 600;
  color: var(--text-secondary);
  margin: 0;
  letter-spacing: -0.02em;
  line-height: 1.1;
}

.close-line-2 {
  font-family: var(--font-display);
  font-size: 3.4rem;
  font-weight: 700;
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  margin: 0;
  letter-spacing: -0.02em;
  line-height: 1.1;
}

.close-cap {
  margin-top: 1.5rem;
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.85;
}
</style>

<!--
S26 · "You didn't read every line. You also didn't ship dark code." The comprehension-debt firewall punchline.

DELIVERY: Land slow. Pause between the two lines. Don't rush to the next slide.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="contract-slide">
  <div class="contract-kicker">the comprehension contract</div>
  <div class="contract-diagram">
    <div class="contract-input">
      <div class="contract-input-label">Plan</div>
      <div class="contract-input-action">creates →</div>
    </div>
    <div class="contract-spec">
      <div class="contract-spec-label">SPEC</div>
      <div class="contract-spec-name">the artifact you understand</div>
    </div>
    <div class="contract-input">
      <div class="contract-input-action">← verifies against</div>
      <div class="contract-input-label">Eval</div>
    </div>
  </div>
  <div class="contract-implement">
    <div class="contract-impl-arrow">↑</div>
    <div class="contract-impl-line"><span class="contract-impl-key">Implement</span> generates code <span class="contract-impl-key">against the spec</span></div>
  </div>
  <p class="contract-caption">You comprehend the spec. <span class="contract-em">The code, you verify.</span></p>
</div>

<style>
.contract-slide {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  align-items: center;
  text-align: center;
}

.contract-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.contract-diagram {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 1.5rem;
  align-items: center;
  width: 100%;
}

.contract-input {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
  align-items: center;
}

.contract-input-label {
  font-family: var(--font-display);
  font-size: 1.85rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

.contract-input-action {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.contract-spec {
  padding: 1.5rem 2.25rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 45%, var(--border));
  border-radius: 0.85rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 78%, var(--vue-green) 22%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  align-items: center;
  box-shadow:
    0 0 30px color-mix(in srgb, var(--vue-green) 22%, transparent),
    inset 0 1px 0 color-mix(in srgb, white 6%, transparent);
}

.contract-spec-label {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  font-weight: 600;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.contract-spec-name {
  font-family: var(--font-display);
  font-size: 1.45rem;
  font-weight: 600;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

.contract-implement {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.4rem;
  margin-top: -0.25rem;
}

.contract-impl-arrow {
  font-family: var(--font-display);
  font-size: 1.5rem;
  color: var(--vue-green);
  opacity: 0.65;
}

.contract-impl-line {
  font-family: var(--font-body);
  font-size: 1.05rem;
  color: var(--text-secondary);
}

.contract-impl-key {
  color: var(--vue-green-light);
  font-weight: 600;
}

.contract-caption {
  font-family: var(--font-display);
  font-size: 1.45rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0.5rem 0 0;
}

.contract-em {
  color: var(--vue-green-light);
  font-weight: 700;
}
</style>

<!--
S27 · "The spec is the comprehension contract." The talk's key callback, brought back to land the close.

DELIVERY:
- "This is the move."
- "You comprehend the spec. The code, you verify. That's how you escape the dichotomy."
- Pause. Then the audio callback.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="beyond-slide">
  <div class="beyond-kicker">beyond the coding harness</div>

  <div class="beyond-grid">
    <div class="beyond-card">
      <div class="beyond-card-tag">DEVOPS · TERMINAL</div>
      <div class="beyond-card-name">Warp Terminal</div>
      <div class="beyond-card-desc">AI-native shell. Pair-programming for ops, scripts, and one-off pipelines.</div>
    </div>
    <div class="beyond-card">
      <div class="beyond-card-tag">INPUT · DICTATION</div>
      <div class="beyond-card-name">Wispr Flow</div>
      <div class="beyond-card-desc">Voice-first dictation. Faster than typing for thinking out loud.</div>
    </div>
    <div class="beyond-card beyond-card-emph">
      <div class="beyond-card-tag">RESEARCH · WEB</div>
      <div class="beyond-card-name">Perplexity</div>
      <div class="beyond-card-desc">AI web search. Citations included. Current knowledge on tap.</div>
    </div>
  </div>

  <p class="beyond-caption">Every layer of the workflow has a tool. <span class="beyond-em">The harness is just where they meet code.</span></p>
</div>

<style>
.beyond-slide {
  max-width: 80rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.beyond-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.beyond-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 0.9rem;
}

.beyond-card {
  padding: 1.4rem 1.3rem;
  border: 1px solid var(--border);
  border-radius: 0.7rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.beyond-card-emph {
  border-color: color-mix(in srgb, var(--vue-green-light) 35%, var(--border));
  box-shadow:
    inset 0 1px 0 color-mix(in srgb, white 5%, transparent),
    0 0 22px color-mix(in srgb, var(--vue-green) 14%, transparent);
}

.beyond-card-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.6rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.beyond-card-emph .beyond-card-tag {
  color: var(--vue-green-light);
}

.beyond-card-name {
  font-family: var(--font-display);
  font-size: 1.55rem;
  font-weight: 700;
  letter-spacing: -0.015em;
  color: var(--text-primary);
}

.beyond-card-desc {
  font-family: var(--font-body);
  font-size: 0.98rem;
  color: var(--text-secondary);
  line-height: 1.5;
}

.beyond-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  font-style: italic;
  margin: 0.2rem 0 0;
  text-align: center;
}

.beyond-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
Beyond the coding harness — three tools I use outside the direct coding loop.

DELIVERY:
- "Quick aside before we close: tools beyond the coding harness."
- Warp Terminal: "AI-native shell. For ops work, deploy scripts, the stuff that lives outside an editor."
- Wispr Flow: "Voice dictation. I think faster than I type — this closes the gap."
- Perplexity (highlighted): "AI web search with citations. Becomes the bridge to the next slide."
- Caption: "Every layer of the workflow has a tool. The harness is just where they meet code."

NEXT SLIDE: drills into Perplexity-as-agent-tool — the Sonar API integration trick.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="px-slide">
  <div class="px-kicker">give your agent <code>Perplexity</code></div>

  <div class="px-flow">
    <div class="px-stage px-stage-stuck">
      <div class="px-stage-tag">01 · agent</div>
      <div class="px-stage-name">stuck or looping</div>
      <div class="px-stage-note">stale training data &middot; unknown lib &middot; new API</div>
    </div>
    <div class="px-arrow">→</div>
    <div class="px-stage px-stage-mid">
      <div class="px-stage-tag">02 · sonar API</div>
      <div class="px-stage-name">web research</div>
      <div class="px-stage-note">current knowledge &middot; cited sources</div>
    </div>
    <div class="px-arrow">→</div>
    <div class="px-stage px-stage-unblocked">
      <div class="px-stage-tag">03 · agent</div>
      <div class="px-stage-name">unblocked</div>
      <div class="px-stage-note">continues the task with fresh context</div>
    </div>
  </div>

  <div class="px-endpoints">
    <div class="px-endpoint">
      <div class="px-endpoint-tag">SONAR</div>
      <div class="px-endpoint-name">quick search</div>
      <div class="px-endpoint-desc">Fast lookup. Latest web context, citations included.</div>
    </div>
    <div class="px-endpoint">
      <div class="px-endpoint-tag">SONAR · REASONING</div>
      <div class="px-endpoint-name">deeper synthesis</div>
      <div class="px-endpoint-desc">Comparative analysis across sources. For harder questions.</div>
    </div>
  </div>

  <p class="px-caption">The agent&rsquo;s <span class="px-em">Stack Overflow</span> &mdash; current knowledge, on demand.</p>
</div>

<style>
.px-slide {
  max-width: 82rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.px-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.px-kicker code {
  font-family: var(--font-mono);
  font-size: 0.95em;
}

.px-flow {
  display: grid;
  grid-template-columns: 1fr auto 1fr auto 1fr;
  gap: 0.5rem;
  align-items: stretch;
}

.px-stage {
  padding: 1rem 1.1rem;
  border: 1px solid var(--border);
  border-radius: 0.6rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
  text-align: center;
  align-items: center;
}

.px-stage-stuck {
  border-color: color-mix(in srgb, #f07178 26%, var(--border));
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, #f07178 8%) 0%,
      var(--bg-elev-1) 100%);
}

.px-stage-mid {
  border-color: color-mix(in srgb, var(--vue-green-light) 38%, var(--border));
  box-shadow:
    inset 0 1px 0 color-mix(in srgb, white 5%, transparent),
    0 0 18px color-mix(in srgb, var(--vue-green) 14%, transparent);
}

.px-stage-unblocked {
  border-color: color-mix(in srgb, #c3e88d 28%, var(--border));
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, #c3e88d 8%) 0%,
      var(--bg-elev-1) 100%);
}

.px-stage-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.6rem;
  font-weight: 600;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.px-stage-stuck .px-stage-tag { color: #f07178; }
.px-stage-mid .px-stage-tag { color: var(--vue-green-light); }
.px-stage-unblocked .px-stage-tag { color: #c3e88d; }

.px-stage-name {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

.px-stage-note {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.68rem;
  letter-spacing: 0.05em;
  color: var(--text-muted);
  line-height: 1.4;
}

.px-arrow {
  display: flex;
  align-items: center;
  font-family: var(--font-display);
  font-size: 1.3rem;
  color: var(--vue-green);
  opacity: 0.65;
}

.px-endpoints {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.7rem;
}

.px-endpoint {
  padding: 0.85rem 1.1rem;
  border: 1px solid var(--border);
  border-radius: 0.55rem;
  background: var(--bg-elev-1);
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
}

.px-endpoint-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.px-endpoint-name {
  font-family: var(--font-display);
  font-size: 1.1rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

.px-endpoint-desc {
  font-family: var(--font-body);
  font-size: 0.85rem;
  color: var(--text-secondary);
  line-height: 1.45;
}

.px-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0.15rem 0 0;
  text-align: center;
}

.px-em {
  color: var(--vue-green-light);
  font-weight: 700;
}
</style>

<!--
Give your agent Perplexity — the Sonar-API-as-agent-tool trick.

DELIVERY:
- "If you take one tactical thing home from this talk, take this."
- Walk the flow: "Agent gets stuck — looping, hallucinating a library, hitting unknown territory. Stale training data, new API, whatever. It calls Sonar. Comes back with current web knowledge and citations. Unblocks itself."
- Walk the two endpoints: "Sonar quick search for fast lookups. Sonar Reasoning for deeper comparative work."
- Land the caption: "The agent's Stack Overflow. Current knowledge, on demand."

WHY THIS LANDS: every developer in the room has hit this loop. Giving the agent a way out is one of the highest-leverage tools you can add to your harness.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="box-slide">
  <div class="box-kicker">what&rsquo;s in the box</div>

  <div class="box-grid">
    <div class="box-row box-row-top">
      <div class="box-card">
        <div class="box-card-tag">SKILL</div>
        <div class="box-card-name">playwright-skill</div>
        <div class="box-card-desc">Real-browser drive for QA + demos. Cross-vendor.</div>
      </div>
      <div class="box-card">
        <div class="box-card-tag">SKILL</div>
        <div class="box-card-name">implementation-skill</div>
        <div class="box-card-desc">Single-agent execute. Cross-vendor.</div>
      </div>
    </div>
    <div class="box-row box-row-bottom">
      <div class="box-card box-card-multi">
        <div class="box-card-tag">PLUGIN · 4 agents</div>
        <div class="box-card-name">spec-gen</div>
        <div class="box-card-desc">Plan: discovery → requirements → design → tasks.</div>
      </div>
      <div class="box-card box-card-multi">
        <div class="box-card-tag">PLUGIN · 5 agents</div>
        <div class="box-card-name">claude-build</div>
        <div class="box-card-desc">Implement: 5 agents in 3 waves.</div>
      </div>
      <div class="box-card box-card-multi">
        <div class="box-card-tag">PLUGIN · 5 agents</div>
        <div class="box-card-name">claude-qa</div>
        <div class="box-card-desc">Validate: 5 auditors, anchored to the spec.</div>
      </div>
    </div>
  </div>

  <div class="box-footer">
    <span class="box-footer-tag">PROGRESSIVE-DISCLOSURE DOCS</span>
    <span class="box-footer-body"><code>backend/docs/conventions/</code> &middot; <code>frontend/docs/conventions/</code> &middot; <code>shared/docs/conventions/</code> &mdash; auto-authored from real evidence</span>
  </div>

  <p class="box-caption">Fork it. Point it at your project. <span class="box-em">Your harness is the layer that comes next.</span></p>
</div>

<style>
.box-slide {
  max-width: 84rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
}

.box-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.box-grid {
  display: flex;
  flex-direction: column;
  gap: 0.65rem;
}

.box-row {
  display: grid;
  gap: 0.65rem;
}

.box-row-top {
  grid-template-columns: 1fr 1fr;
}

.box-row-bottom {
  grid-template-columns: 1fr 1fr 1fr;
}

.box-card {
  padding: 0.85rem 1.1rem 0.95rem;
  border: 1px solid var(--border);
  border-radius: 0.55rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.box-card-multi {
  border-color: color-mix(in srgb, var(--vue-green-light) 22%, var(--border));
}

.box-card-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.6rem;
  font-weight: 600;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.85;
}

.box-card-name {
  font-family: var(--font-mono);
  font-size: 1.15rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
}

.box-card-desc {
  font-family: var(--font-body);
  font-size: 0.85rem;
  color: var(--text-secondary);
  line-height: 1.4;
}

.box-footer {
  padding: 0.6rem 1rem;
  border: 1px dashed color-mix(in srgb, var(--vue-green-light) 28%, var(--border));
  border-radius: 0.5rem;
  background: var(--bg-elev-1);
  display: flex;
  align-items: baseline;
  flex-wrap: wrap;
  gap: 0.5rem 0.85rem;
}

.box-footer-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.box-footer-body {
  font-family: var(--font-body);
  font-size: 0.82rem;
  color: var(--text-secondary);
}

.box-footer-body code {
  font-family: var(--font-mono);
  font-size: 0.88em;
}

.box-caption {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0.2rem 0 0;
  text-align: center;
}

.box-em {
  color: var(--vue-green-light);
  font-weight: 700;
}
</style>

<!--
What's in the box — recap of harness-visualizer contents.

DELIVERY:
- "Quick recap. When you fork harness-visualizer, here's what you get."
- Skills first (top row): "playwright-skill — real-browser drive, works in both Claude Code and pi.dev. implementation-skill — single-agent executor, also cross-vendor."
- Plugins next (bottom row): "spec-gen for plan, claude-build for implement, claude-qa for validate. Three plugins, the whole spec-driven loop."
- Point at the dashed footer: "Plus the auto-authored convention docs for backend, frontend, and shared. Real path:line evidence."
- Land the caption: "Fork it. Point it at your project. Your harness is the layer that comes next."

WHY THIS LANDS: every CTA needs a "what do I actually get" — this slide is that answer in concrete form.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="build-slide">
  <p class="build-headline">Don&rsquo;t wait for the perfect tool.</p>
  <p class="build-sub">Build the harness for the next feature, <span class="build-em">today</span>.</p>
  <div class="build-repos">
    <div class="build-repo">
      <div class="build-repo-tag">DEMO VEHICLE</div>
      <div class="build-repo-name">harness-visualizer</div>
      <div class="build-repo-desc">Point at any project. See its harness.</div>
    </div>
    <div class="build-repo">
      <div class="build-repo-tag">REUSABLE</div>
      <div class="build-repo-name">vue-agentic-harness</div>
      <div class="build-repo-desc">The reusable harness for Vue 3 projects.</div>
    </div>
  </div>
</div>

<style>
.build-slide {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  align-items: center;
  text-align: center;
}

.build-headline {
  font-family: var(--font-display);
  font-size: 2.3rem;
  font-weight: 600;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.015em;
}

.build-sub {
  font-family: var(--font-display);
  font-size: 2.6rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0;
  letter-spacing: -0.02em;
  line-height: 1.1;
}

.build-em {
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.build-repos {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  width: 100%;
  margin-top: 1.5rem;
}

.build-repo {
  padding: 1.5rem 1.5rem;
  border: 1px solid color-mix(in srgb, var(--vue-green-light) 30%, var(--border));
  border-radius: 0.75rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 90%, var(--vue-green) 10%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  align-items: center;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 5%, transparent);
}

.build-repo-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.build-repo-name {
  font-family: var(--font-mono);
  font-size: 1.45rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
}

.build-repo-desc {
  font-family: var(--font-body);
  font-size: 0.98rem;
  color: var(--text-secondary);
}
</style>

<!--
S29 · "Build your harness today." Empowerment + repo CTAs.

DELIVERY:
- "Don't wait for the perfect tool."
- "Build the harness for the next feature, today."
- "Both repos are public. Star them, fork them — tell me what your harness looks like."

ASSETS: add QR codes for each repo when URLs finalize.
-->

---
layout: default
class: '!justify-center'
transition: fade
---

<div class="qr-slide">
  <div class="qr-kicker">scan · fork · point at your project</div>

  <div class="qr-content">
    <div class="qr-card">
      <img :src="`${$slidev.configs.base || '/'}repo-qr.png`" alt="QR code linking to the harness-visualizer GitHub repo" />
    </div>
    <div class="qr-info">
      <div class="qr-tag">REPO</div>
      <div class="qr-name">harness-visualizer</div>
      <p class="qr-desc">Every skill, every plugin, every progressive-disclosure doc &mdash; <span class="qr-em">all of it</span>.</p>
      <p class="qr-desc qr-desc-sub">Fork it. Point it at your project. Build your harness on top.</p>
    </div>
  </div>
</div>

<style>
.qr-slide {
  max-width: 78rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.qr-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
  text-align: center;
}

.qr-content {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 2.75rem;
  align-items: center;
  justify-content: center;
}

.qr-card {
  width: 22rem;
  height: 22rem;
  padding: 1rem;
  background: #ffffff;
  border-radius: 0.75rem;
  box-shadow:
    0 14px 44px rgba(0, 0, 0, 0.45),
    0 0 30px color-mix(in srgb, var(--vue-green) 18%, transparent);
  display: flex;
  align-items: center;
  justify-content: center;
}

.qr-card img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.qr-info {
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
  max-width: 32rem;
}

.qr-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.qr-name {
  font-family: var(--font-mono);
  font-size: 2.3rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.02em;
  line-height: 1;
}

.qr-desc {
  font-family: var(--font-display);
  font-size: 1.3rem;
  font-weight: 500;
  color: var(--text-primary);
  margin: 0;
  line-height: 1.4;
}

.qr-desc-sub {
  color: var(--text-secondary);
  font-weight: 400;
  font-size: 1.1rem;
}

.qr-em {
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 700;
}
</style>

<!--
QR slide · scan to fork the harness-visualizer repo.

DELIVERY:
- "If you want to actually USE any of this — here's the repo."
- "harness-visualizer. Every skill, every plugin, every convention doc we walked through."
- "Fork it. Point it at your project. Build your harness on top."
- Hold the slide. Let people scan. 10-15 seconds.
- Then advance to thanks.
-->

---
layout: default
class: '!justify-center text-center'
transition: fade
---

<div class="thanks-slide">
  <div class="thanks-logo">
    <BaLogo />
  </div>
  <h1 class="thanks-name">Will Marple</h1>
  <div class="thanks-tagline">Distinguished Engineer · Black Airplane</div>
  <div class="thanks-linkedin-tag">connect on linkedin</div>
  <div class="thanks-linkedin">
    <img :src="`${$slidev.configs.base || '/'}linkedin-qr.png`" alt="QR code linking to Will Marple's LinkedIn profile" />
  </div>
  <p class="thanks-q">Questions?</p>
</div>

<style>
.thanks-slide {
  max-width: 60rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.thanks-logo {
  display: flex;
  justify-content: center;
  margin-bottom: 1rem;
}

.thanks-name {
  font-family: var(--font-display) !important;
  font-size: 3.5rem !important;
  font-weight: 700 !important;
  color: var(--text-primary) !important;
  margin: 0 !important;
  letter-spacing: -0.025em;
  line-height: 1;
}

.thanks-tagline {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--vue-green-light);
}

.thanks-linkedin-tag {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.62rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--text-muted);
  margin-top: 0.75rem;
}

.thanks-linkedin {
  width: 7.5rem;
  height: 7.5rem;
  padding: 0.4rem;
  background: #ffffff;
  border-radius: 0.55rem;
  box-shadow:
    0 8px 24px rgba(0, 0, 0, 0.45),
    0 0 18px color-mix(in srgb, var(--vue-green) 16%, transparent);
  display: flex;
  align-items: center;
  justify-content: center;
}

.thanks-linkedin img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.thanks-q {
  margin-top: 2rem;
  font-family: var(--font-display);
  font-size: 2.4rem;
  font-weight: 700;
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  letter-spacing: -0.02em;
}
</style>

<script setup>
import BaLogo from './components/BaLogo.vue'
</script>

<!--
S30 · Thank you / Q&A.

DELIVERY:
- "Thank you."
- "I'll be at the break. Find me — I want to hear what your harness looks like."
-->
