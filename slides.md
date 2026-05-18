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

<div class="skip-slide">
  <div class="skip-kicker">First stop: Prompting</div>

  <p class="skip-line">You're already good at this.</p>

  <p class="skip-sub">Walking past — the interesting work is downstream.</p>
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

<div class="pd-slide">
  <div class="pd-kicker">02 · Context — progressive disclosure</div>
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
  <p class="pd-caption">Each step narrows what the next agent sees — the <span class="pd-em">smallest possible context</span>.</p>
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
Context lever, stop 2: the architecture — multi-agent research feeding the sequential pipeline.

DELIVERY:
- "Context isn't just one file. It's a discipline of revealing only what the next step needs."
- Point at the dashed research box: "It starts with parallel research. Three agents go simultaneously — research-lead, integration-researcher, codebase-explorer."
- "Their output feeds into discovery. From there, the pipeline runs sequentially."
- Walk the four stops: discovery → requirements → design → tasks. Note discovery has the green border because it's the receiving step.
- Land the caption: "Each step narrows what the next agent sees — the smallest possible context."

NEXT SLIDE: the vendor-portability beat. Same pipeline exists as a Claude Code plugin AND a pi.dev skill — but only Claude Code can do the multi-agent orchestration.
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
      <div class="vp-cap vp-cap-no">— no multi-agent (platform limit)</div>
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
  gap: 1.5rem;
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
  font-size: 1.85rem;
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
  padding: 1.4rem 1.25rem;
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 92%, var(--vue-green) 8%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.65rem;
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
  font-size: 1.55rem;
  font-weight: 700;
  color: var(--text-primary);
  letter-spacing: -0.01em;
  margin: 0.1rem 0 0.3rem;
}

.vp-agents {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}

.vp-agent {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.78rem;
  color: var(--text-secondary);
  padding: 0.3rem 0.55rem;
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
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  margin-top: 0.4rem;
  padding-top: 0.55rem;
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

<div class="tools-slide">
  <div class="tools-kicker">04 · Tools — what the agent can actually do</div>

  <div class="tools-grid">
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
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.85rem;
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
- Walk the four cards. Skills first (single-purpose), plugins next (multi-agent orchestrations).
- The closing line is the point: "Each tool was built to fit THIS project's grain." — not off-the-shelf, not generic.
- Next slide drills into Playwright as a worked example.
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

<div class="eval-slide">
  <div class="eval-kicker">05 · Evaluation — the loop closes</div>

  <div class="eval-grid">
    <div class="eval-card">
      <div class="eval-num">01</div>
      <div class="eval-name">Behavioral</div>
      <div class="eval-tool">playwright-skill</div>
      <div class="eval-desc">Does it do the thing? Drive the real browser. Verify the actual page state matches the spec.</div>
    </div>
    <div class="eval-card">
      <div class="eval-num">02</div>
      <div class="eval-name">Structural</div>
      <div class="eval-tool">architect-reviewer</div>
      <div class="eval-desc">Is it built the right way? A subagent reads the diff against the design doc. Flags drift.</div>
    </div>
  </div>

  <p class="eval-caption">Both verify the implementation against <span class="eval-em">the spec</span> — the comprehension contract.</p>
</div>

<style>
.eval-slide {
  max-width: 70rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  gap: 1.75rem;
}

.eval-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.eval-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.eval-card {
  padding: 1.75rem 1.5rem;
  border: 1px solid var(--border);
  border-radius: 0.75rem;
  background:
    linear-gradient(180deg,
      color-mix(in srgb, var(--bg-elev-1) 90%, var(--vue-green) 10%) 0%,
      var(--bg-elev-1) 100%);
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  box-shadow: inset 0 1px 0 color-mix(in srgb, white 4%, transparent);
}

.eval-num {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  color: var(--vue-green-light);
  opacity: 0.75;
}

.eval-name {
  font-family: var(--font-display);
  font-size: 1.85rem;
  font-weight: 700;
  letter-spacing: -0.015em;
  color: var(--text-primary);
}

.eval-tool {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  color: var(--vue-green-light);
  font-weight: 500;
}

.eval-desc {
  font-family: var(--font-body);
  font-size: 1rem;
  color: var(--text-secondary);
  line-height: 1.5;
  margin-top: 0.25rem;
}

.eval-caption {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}

.eval-em {
  color: var(--vue-green-light);
  font-style: normal;
  font-weight: 600;
}
</style>

<!--
Evaluation lever, stop 1: the two-layer eval pattern.

DELIVERY:
- "The evaluation lever is what closes the loop. It's also what answers the comprehension question."
- Two cards: behavioral (does it work?) and structural (is it right?).
- "Playwright verifies the page does what the spec says it should. The architect-reviewer subagent verifies the code matches the design we agreed on."
- Land on the caption: "Both verify against the spec — the comprehension contract."
- This is where the spec-is-the-comprehension-contract idea gets its operational payoff.
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
-->

---
layout: default
class: '!justify-center text-center'
transition: fade
---

<div class="demo-tee-slide">
  <div class="demo-tee-kicker">Now watch it work</div>

  <h1 class="demo-tee-line">
    <span class="demo-step">Plan</span>
    <span class="demo-arrow">→</span>
    <span class="demo-step">Implement</span>
    <span class="demo-arrow">→</span>
    <span class="demo-step">Validate</span>
  </h1>

  <p class="demo-tee-sub">One feature, added to the visualizer, end-to-end.</p>
</div>

<style>
.demo-tee-slide {
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.demo-tee-kicker {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--vue-green-light);
  opacity: 0.9;
}

.demo-tee-line {
  font-family: var(--font-display) !important;
  font-size: 4rem !important;
  font-weight: 700 !important;
  margin: 0 !important;
  display: flex;
  align-items: baseline;
  gap: 1.25rem;
  letter-spacing: -0.02em;
  line-height: 1 !important;
}

.demo-step {
  background: linear-gradient(110deg, var(--vue-green-light) 0%, var(--vue-blue) 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.demo-arrow {
  color: var(--vue-green);
  opacity: 0.6;
  font-weight: 400;
  font-size: 2.5rem;
}

.demo-tee-sub {
  font-family: var(--font-body);
  font-size: 1.3rem;
  color: var(--text-secondary);
  margin: 0;
  font-style: italic;
}
</style>

<!--
Transition slide into the demo. The tour just ended; now the levers fire in sequence.

DELIVERY:
- Don't read the slide. Let it land.
- "All four levers, in motion, on one feature."
- Then start the demo.
- This is the highest-energy moment of the talk so far. Earn it.
-->
