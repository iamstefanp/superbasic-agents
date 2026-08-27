━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Running a SuperBasic™ Agent

WHAT: The four surfaces a SuperBasic™ Agent runs on, what each one gives you,
      and what each one costs you.
WHY:  An agent that only runs where its author runs it is a document, not a
      product. The same constitution has to work in a terminal, in a browser,
      pasted into a chat window, and unattended overnight — and the honest
      differences between those need stating rather than hiding.
WHO:  Anyone who has downloaded an agent and wants to use it. Anyone deciding
      which surface a given job belongs on.
HOW:  §1 helps you pick. §2–§5 are the four surfaces, each self-contained —
      read only the one you need. §6 is what changes and what doesn't.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. PICKING A SURFACE

The same agent runs four ways. They are not tiers of quality — they are
different trades between capability, effort, and how much of the method
survives.

  SURFACE            YOU GET                        YOU GIVE UP
  ─────────────────────────────────────────────────────────────────────────
  Claude Code        Tools, files, a pinned model,  A terminal. Setup.
                     persistent memory, hooks that
                     can actually enforce gates

  claude.ai          One upload, works everywhere   Tools beyond what the
                     the browser does, no setup     host provides

  Paste-anywhere     Works in any chat window,      Progressive disclosure,
                     any model, zero install        auto-triggering, length

  Unattended         Runs with nobody watching,     Judgment in the moment.
  (workflow engine)  continuously, on a schedule    Everything must be
                     or an event                    decided in advance

Rules of thumb:

  — A job someone starts and watches → Claude Code or claude.ai.
  — A job that must happen whether or not anyone is awake → unattended.
  — Trying a method out before committing to it → paste-anywhere.
  — Anything touching real credentials or irreversible actions → unattended,
    and read §5 carefully before you build it.

2. SURFACE ONE — CLAUDE CODE

The fullest version. The agent gets tools, a pinned model, its own context,
and — uniquely — a harness that can enforce its gates rather than advising
them.

Install:

    cp -r agents/researcher ~/.claude/skills/superbasic-researcher

Or point at the repo directly if your setup supports it. The agent appears by
the `name` in its frontmatter (`superbasic-researcher`) and can be invoked by
name or triggered by its `description` matching what you asked for.

The `subagent.md` variant:

  `compiled/subagent.md` is the Claude Code build. It carries what only this
  harness can honour — a tool allowlist, a model pin, isolated context so the
  agent's work does not pollute the main conversation, and persistent memory
  across runs. Use it when the agent should run as a sub-task rather than
  taking over the conversation.

What this surface uniquely offers: **enforcement**. Everywhere else, a gate
is a promise the agent makes to itself. Here a hook can refuse the write.
If a gate genuinely matters — not "should" but "must" — this is the only
surface that can hold it.

3. SURFACE TWO — CLAUDE.AI

Upload the agent's folder as a Skill. It becomes available in your
conversations without any local setup.

  1. Zip the agent folder (the one containing `SKILL.md`)
  2. Upload it in your Skills settings
  3. Invoke by name, or let the description trigger it

One hard constraint, and it is worth knowing before you edit anything: the
`SKILL.md` frontmatter must carry **only** the spec fields — `name`,
`description`, `license`, `compatibility`, `metadata`, `allowed-tools`. A
single Claude-Code-only key and the upload fails with a hard error. This is
why `subagent.md` exists as a separate file rather than as extra keys in
`SKILL.md`.

Keep `description` at 200 characters or under. The documentation is
inconsistent about the true ceiling; 200 is the safe floor.

4. SURFACE THREE — PASTE ANYWHERE

`compiled/plain.md` is the whole agent flattened into one block you can paste
into any chat window, with any model, with no install path at all.

**It is lossy, and we say so.** What you lose:

  — Progressive disclosure. Everything loads at once; nothing is fetched on
    demand. Long references get cut rather than deferred.
  — Auto-triggering. Nothing recognises when the agent should engage. You
    invoke it by pasting it.
  — Length headroom. A context window spent on the agent is context not
    spent on the work.

What survives: the Iron Law, the Method, the Gates, the Failure Modes, the
Voice. The parts that make the output recognisably SuperBasic™ are the parts
that travel — which is the point.

Treat this surface as a demonstration, not the product. It is how someone
finds out whether a method is worth installing.

5. SURFACE FOUR — UNATTENDED, IN A WORKFLOW ENGINE

The agent runs with nobody in the room. A message arrives, a schedule fires,
a webhook triggers — and the agent does its work and files the result.

This is a genuinely different mode, not a fourth install path, and it changes
what the constitution has to do. Everywhere else, an agent that is uncertain
can ask its one question and wait. Here there is no one to ask. Every
judgment has to be pre-made, and every capability the agent should not have
must be **absent**, not merely forbidden.

5.1 THE PATTERN — engine-agnostic

Any workflow engine works: n8n, Make, Zapier, a cron job calling an API, a
queue worker you wrote yourself. The pattern is the same and worth learning
independently of any vendor:

  TRIGGER      What wakes the agent. An event, a schedule, a webhook.

  FETCH        Get the thing to work on, plus the agent's own prompt.

  DECIDE       One model call. The agent's compiled prompt as the system
               message, the item as the input, structured output back.

  ACT          Do the bounded things — file, tag, route, record. Only the
               actions that exist in the graph can happen.

  LOG          Write what happened and why. Every run, not just failures.

5.2 THE LIVE PROMPT — one source of truth

The single most useful decision in this mode: **do not paste the agent's
prompt into the engine.** Fetch it at the start of every run from wherever it
actually lives — a document, a file, an endpoint.

Pasted, the prompt and its source drift apart the moment either is edited
alone, and nobody notices until output goes strange weeks later. Fetched,
editing the source *is* editing the agent — no redeploy, no version
mismatch, no second copy to keep honest. It costs one call per run.

The constitution is not fetched. It is the source the prompt compiles from,
read by humans at build time, and it never enters the runtime path.

5.3 PERMISSIONS ARE STRUCTURAL, NOT CONDITIONAL

An agent that must never send email should not be *asked* not to send email.
The send step should not exist in the graph.

This is the difference between a rule and a fact. A rule lives in the prompt
and depends on the model honouring it under every phrasing anyone will ever
send. A fact lives in the topology: there is no send node, therefore nothing
can send, regardless of what the model decides.

  Irreversible actions — send, delete, publish, pay, transfer:
    Either the capability exists in the graph or it does not. Never gate one
    of these on a runtime condition someone can edit.

  Reversible actions — tag, file, route, draft, record:
    These may reasonably read a configuration value and switch between
    "do it" and "propose it." A wrong tag is a correction; a wrong send is
    an incident.

Write the setting down as a literal value — `send: disabled`, `file: auto` —
not as a sentence in a document. A sentence is a hope. A value is a
configuration, and a missing node is a guarantee.

5.4 MEMORY — usually smaller than you think

Most unattended agents do not need to learn anything. They need to not do
the same thing twice.

That is idempotency, not memory: before acting, check whether this item's
stable identifier already appears in the record the agent writes to. If it
does, stop. The record the agent produces *is* its memory, and no separate
store is required.

Genuine cross-run memory — an agent that gets better because of what it saw
last week — is a real need for some archetypes and an unnecessary complexity
for most. Decide it per agent, deliberately. Do not provision a memory store
by default.

5.5 THE HONEST COST

Unattended is the mode where mistakes compound quietly. An agent that
mis-files one message a day is invisible for a month and then represents a
month of mis-filing.

Two things make it survivable, and both belong in the build rather than in
good intentions:

  — Every run logs, including the runs where nothing happened. A silent
    success and a silent failure look identical.
  — Something watches the watcher. If the agent has not run in longer than
    its trigger interval, that is a failure state and must announce itself.
    An automation that fails silently is worse than no automation, because
    it is trusted.

6. WHAT CHANGES AND WHAT DOESN'T

Across all four surfaces, these are constant — and they are what makes the
output recognisably SuperBasic™ regardless of where it ran:

  — The Iron Law
  — The Method's named moves, in order
  — The Gates, and PARTIAL when one fails
  — Golden Words on every claim
  — RPP: relay what was understood, plan what will be done, prove it after
  — Velcro on every document produced

These change by surface:

  — Tools available
  — Whether gates are enforced or advisory
  — Whether the agent can ask its one question, or must decide alone
  — How much reference depth loads upfront versus on demand

**The honest limit, stated rather than buried:** once distributed, a
constitution is advisory. In Claude Code a pack can ship hooks that enforce.
In an unattended graph, topology enforces. Everywhere else, drift is made
*visible* rather than impossible — Golden Words missing, RPP skipped, a flat
assertion where a tier should be. We do not claim more than that.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VELCRO FOOTER

WHEN
  Version: 1.0 | Date: 2026-08-27

WHERE
  Repo: superbasic-agents/docs/RUNNING-AN-AGENT.md

WHICH
  Related Documents: SuperBasic™ Agent Standard (§4 compilation, §6 trust
    posture) · Creating an Agent Type · constitution-template.md

VALID?
  Intention: Make every deployment surface usable by someone who has only
    downloaded the repo, including the unattended one, without binding the
    method to any vendor.
  Research: Vendor-pattern verification run 2026-08-27 (Zapier · Make ·
    n8n · Lindy · Beam AI · monday.com · Okta · Microsoft) — the
    trigger/prompt/connections/permissions/log shape is consistent across
    all of them.
  Synthesis: §5 generalises that shape; §5.3 and §5.5 are the two places
    the surveyed products most often get it wrong.
  Analysis: Full.
  Status: MET
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
