## Rodrigo Paisana

**I design AI workflows for ops teams.** Prompt and context engineering, guardrails, and systems that stay
reliable when things go wrong.

Lisbon · open to remote AI ops / automation roles

---

### What I actually do

I work in B2B/B2C support at a cybersecurity company. A while back I started building the AI system I now use to
do that job — and building those systems turned out to be the thing I'm good at.

The interesting problem in all of it is the same one: **an AI that's confidently wrong is worse than no AI at
all.** Everything below is about that.

---

### Production AI support system
*Not public — it's my employer's internal tooling. Happy to walk through the design.*

A Claude project I designed and maintain: a ~4,000-word operational instruction architecture over a ~100-document
grounded knowledge base, used daily to triage and resolve real tickets.

**Sourcing discipline, built entirely in prompt and context** — knowledge-base-over-logic grounding, explicit
authority and scope gates, a *"never assert an absence as fact"* rule, and a protocol forcing live verification of
anything volatile. Anti-hallucination as architecture, not as an afterthought.

**A self-improving correction loop** — real mistakes captured as generalisable rules and folded back weekly, with
conflict detection and pruning so the instructions don't rot.

**A mode-based interface** — email / chat / call / log. One brain, different structured output per channel.

Cut my per-ticket handling from roughly 10–20 minutes to 3–5. *Estimated from my own throughput, not formally measured.*

---

### [scene-intel](https://github.com/berbotu/scene-intel) — the same discipline, in public

A scheduled AI research agent. **No code** — a prompt, a schedule, and a set of guardrails.

Every claim must carry a source URL or it doesn't get written. It writes only to a staging file it can't confuse
with canonical data. It commits exactly one file. Zero connectors — it reads the open web, and a web-reading agent
with write access to your email is how prompt injection stops being theoretical.

**On its first run, three of five sources returned 403.** It reported the gap and marked the sources unretrievable
rather than inventing a plausible answer — then diagnosed its own network limits unprompted.

That's the part worth looking at. Every portfolio has a demo that worked. **A guardrail that only holds when
everything works isn't a guardrail.**

---

### [berbotu-mcp](https://github.com/berbotu/berbotu-mcp) — wiring an AI to a live system without it breaking things

A typed MCP server letting an AI read and write real records in a live repository.

Every write lands as its own auditable, reversible git commit. Existence is SHA-checked before anything is touched.
Each tool carries explicit `destructive` / `idempotent` annotations so the model knows what it can safely call.
Rolled out read-only first; writes enabled only once the guardrails held.

*~1,000 lines of TypeScript, AI-assisted. I'm not an engineer and I'm not trying to be — I'm someone who knows what
to build and how to keep it from breaking things.*

---

### [Berbotu](https://berbotu.com) — the label all of this runs against

Hard Trance / Hard Bounce label out of Lisbon. 11 releases. I run it, and it's the system I build against — every
tool above solves a problem it actually had. Site is mid-redesign.

---

**The thread:** "I built it with AI" isn't a skill anymore — everyone has that. What's scarce is knowing *what* to
build, making it reliable, and operating it for months against real work.

[LinkedIn](https://linkedin.com/in/rodrigo-paisana)
