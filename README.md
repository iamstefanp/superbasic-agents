# SuperBasic™ Agents

**AI that works to a method, not a vibe.**

Most AI agents are a personality and a wish. These carry a methodology — an
absolute rule they will not cross, gates that can actually fail, and a habit
of telling you how sure they are and why.

Built by [Stefan Petcov](https://runwayservices.net) / Runway Services, from
the SuperBasic™ methodology. Free to use and adapt.

---

## Available now

Six agents. Each carries one absolute rule it will not cross.

**[Researcher](agents/researcher/compiled/SKILL.md)** — research you can
check. Briefs before gathering, tiers every source, reports what it *didn't*
find.
*No claim without a source you can check, and no source without a tier.*

**[Interviewer](agents/interviewer/compiled/SKILL.md)** — draws out what you
actually want before anything gets built. Pushes past the first abstract
answer.
*One question at a time. Never a list.*

**[Designer](agents/designer/compiled/SKILL.md)** — designs from real
references, not adjectives. Gathers what you already admire before proposing
anything.
*No design decision without a reference it traces back to.*

**[Developer](agents/developer/compiled/SKILL.md)** — builds in slices you
can see, states the cost of every decision.
*No "done" without fresh proof, and no decision without its cost.*

**[Reviewer](agents/reviewer/compiled/SKILL.md)** — checks work against what
was agreed, adversarially, with fresh eyes.
*You report, you do not repair.*

**[Management](agents/management/compiled/SKILL.md)** — keeps work
traceable. Opens it properly, closes it so someone cold can pick it up.
*Nothing is done until someone else could find it.*

In progress: Writer · Strategist · Promoter · Sales.

---

## Install

**claude.ai** — download the agent folder, zip it, then Settings →
Customize → Skills → upload. No terminal needed.

**Claude Code** — copy the folder into `~/.claude/skills/`:

```bash
git clone https://github.com/iamstefanp/superbasic-agents.git
cp -r superbasic-agents/agents/researcher/compiled ~/.claude/skills/superbasic-researcher
```

**Anywhere else** — the `SKILL.md` is plain markdown. Paste it into any chat
that accepts a system prompt. It works in ChatGPT, Gemini, Cursor, and
anything reading the Agent Skills standard.

---

## What makes these different

**An Iron Law.** One absolute per agent. The Researcher will not present a
claim without a checkable source. Not a preference — the line it doesn't
cross.

**Gates that can fail.** Four checks before a run counts as done. Fail one and
the output is marked PARTIAL, honestly, rather than dressed up as complete. A
gate that can't fail isn't a gate.

**Calibrated language.** Every claim carries CONFIRMED, LIKELY, ESTIMATED, or
UNKNOWN. You always know whether you're holding a fact or a guess — and it's
also the tell: an agent asserting everything flatly has drifted.

**Pre-answered excuses.** Each agent carries a list of the rationalizations it
will generate — *"I already know this, no need to check"* — with the answer
written next to it, so it reads its own excuse pre-refuted.

**No scripts, nothing executable.** Plain markdown you can read start to
finish before installing. Given that audits have found 12–36% of skills in
public registries carrying security issues, mostly delivered through
executable "prerequisites" — that matters.

---

## Structure

```
commons/              written once, carried by every agent
  principles.md         the 8 SuperBasic principles
  rpp.md                relay · plan · proof
  golden-words.md       confirmed / likely / estimated / unknown
  velcro.md             what · why · who · how
  skills/               the practices agents carry

agents/researcher/
  constitution.md       the source of truth — hand-written
  voice/                exemplars + ban list
  compiled/SKILL.md     the installable artifact — generated
```

Each agent is written once in its constitution. Everything distributed is
compiled from it.

---

## License

Agent definitions: **CC BY-SA 4.0** — use them, adapt them, build on them.
Share adaptations under the same terms.

**SuperBasic™** is a trademark. The method is open; the name is not. See
[TRADEMARK.md](TRADEMARK.md).
