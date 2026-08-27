━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Creating a SuperBasic™ Agent Type

WHAT: How to constitute a new archetype — a kind of agent that does not yet
      exist — rather than deploying one that does.
WHY:  Ten archetypes cover a lot and will not cover your domain. A method
      that only works for its author's ten roles is a product; one that lets
      you build the eleventh is a standard. This is the eleventh.
WHO:  Anyone adding an archetype to their own roster. Read the Standard
      first — this says in what ORDER, the Standard says WHAT.
HOW:  §1 first, always — most new-agent ideas are existing agents wearing a
      hat, and finding that out costs five minutes instead of a week. Then
      §2–§7 in order. Do not skip to writing.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

0. TYPE VERSUS INSTANCE

Two different things get called "making an agent," and confusing them wastes
the most time:

  A TYPE (archetype) is a kind of agent. The Researcher. Written once,
  exists forever, not bound to any particular job. This document.

  An INSTANCE is a type put to work on something specific — this mailbox,
  this account, this client. Deploying an instance is not covered here;
  it is a matter for whoever is running the agent, and it does not require
  a new type.

If what you need is "the Researcher, but for my industry," you almost
certainly need an instance with different reference material, not a new
archetype. Read §1.

1. THE DUPLICATE CHECK — do this before anything

Most proposed archetypes are existing archetypes with a domain attached.
Building the duplicate costs you a second thing to maintain, a roster that
no longer explains itself, and users who cannot tell which one to reach for.

Read every archetype currently on your roster. For each, ask: **does the
proposed role overlap meaningfully with this one?**

  Overlap above ~70%     STOP. Extend the existing archetype's scope, or
                         deploy it as an instance with new references.
                         Do not create.

  Overlap 30–70%         Surface it. Name the close matches explicitly and
                         decide deliberately, in writing, why this is
                         genuinely a different role rather than a variant.

  Overlap below 30%      Proceed.

The sharpest test is not what the agent *does* — many agents do overlapping
things. It is **what it refuses to do**. Two archetypes with the same
refusals are one archetype. If your proposed agent's refusal list is a subset
of an existing agent's, you have found a variant, not a species.

The second test: can you name at least two tasks that fall *outside* your new
archetype and say which existing archetype owns each? If you cannot, the
boundary is not real yet.

2. NAME IT

The name is the role, not a product name and not a personality. Researcher.
Reviewer. Promoter. A stranger reading only the name should be able to guess
roughly what it refuses to do.

Avoid: invented words, mascot names, anything requiring explanation before it
means something. The Standard's roster is deliberately plain — that plainness
is what makes it portable across languages, industries, and companies that
already have their own vocabulary.

If your organisation uses internal codes, keep them in your own registry.
They do not belong in the archetype's own files, which should survive being
copied out of your organisation entirely.

3. WRITE THE CONSTITUTION — in this order

Start from `templates/constitution-template.md`. Fill it in this sequence,
which is not the order the sections appear in:

  1. IRON LAW first.
     Before anything else, name the one thing this agent must never do. If
     you cannot write it in one line, in capitals, you do not yet know what
     the agent is for. Everything else calibrates against this.

  2. SCOPE second — especially the out-of-scope half.
     Two items minimum, each naming the archetype that owns it. This is
     where §1's duplicate check gets written down permanently.

  3. CARRIES third.
     What methodology does this agent actually run? If the answer is "it's
     just good at X," you have a persona, not an agent. A practice has
     named steps someone else could follow. Put shared practices in
     `commons/skills/` — never write the same practice twice.

  4. METHOD fourth.
     The named moves, in order, invoking what CARRIES named. Each move is
     an instruction, not a description of a phase.

  5. GATES fifth.
     What must be true before "done." Each gate names a proving action —
     something the agent must actually do, not something it must feel
     confident about. A gate satisfiable by believing it is satisfied is
     decoration.

  6. RATIONALIZATION sixth, and take it seriously.
     Write the excuses this agent will invent, in its own likely words, each
     with its rebuttal. The excuses that matter are the reasonable-sounding
     ones. This is the section most often written thinly and the one that
     does the most work against drift — the agent meets its own excuse
     already refuted.

  7. FAILURE MODES seventh.
     All five, always, adapted to this archetype. Never drop one.

  8. OUTPUT eighth.
     What finished work looks like, concretely, plus the completion stamp.

  9. VOICE ninth — see §4, it is not written here.

  10. IDENTITY last.
      Counter-intuitive and reliable: you rarely know what an agent *is*
      until you have written what it refuses to do and how it works. Written
      first, IDENTITY becomes an aspiration the rest fails to live up to.
      Written last, it is a summary of something real.

      Keep it thin. Three lines and a refusal sentence.

4. BUILD THE VOICE KIT

Voice is carried by examples and bans. Never by adjectives.

`voice/exemplars.md` — three to five before/after passages. Take real writing
this archetype would produce, show the version that drifts, show the version
that does not, and say in one line what changed. Examples teach what
"authoritative but not pompous" cannot.

`voice/banlist.md` — the constructions this agent never uses. Be specific
enough to check: not "avoid corporate language" but the actual phrases.

If you find yourself writing adjectives into the constitution's VOICE
section, the voice kit is not doing its job yet.

5. COMPILE

One source, multiple artifacts. Never hand-edit inside `compiled/` — it will
be overwritten and the fix will be lost.

  compiled/SKILL.md      The product. Frontmatter carries ONLY the spec
                         fields: name, description, license, compatibility,
                         metadata, allowed-tools. One non-spec key and a
                         claude.ai upload fails hard. Description ≤200
                         characters. Body under 500 lines. Commons compiled
                         IN so the file stands alone.

  compiled/subagent.md   The Claude Code build — tool allowlist, model pin,
                         isolated context, persistent memory.

  compiled/plain.md      The paste-anywhere flatten. Lossy, and labelled so.

Deployment to an unattended workflow engine compiles from the same source —
see `RUNNING-AN-AGENT.md` §5.

6. CHECK IT AGAINST THE FOUR TELLS

Before you call it done, verify the agent is verifiably SuperBasic™ — these
are readable by an outsider, which is the point:

  ☐ Golden Words on every claim (CONFIRMED · LIKELY · ESTIMATED · UNKNOWN).
    An agent asserting flatly has drifted, and the drift is visible.
  ☐ RPP on every action — relay what was understood, plan what will be
    done, prove it after. Never a bare "done."
  ☐ Velcro on every document it produces.
  ☐ Asks before assuming. One question, not a list.

And against the Standard's own structural rules:

  ☐ Ten sections present, none deleted ("None" where inapplicable)
  ☐ Exactly one Iron Law, in capitals
  ☐ At least two out-of-scope items, each naming an owning archetype
  ☐ Every CARRIES entry points to a real file
  ☐ No practice written twice — shared ones live in commons/
  ☐ Nothing in `compiled/` was hand-edited

7. THE STRANGER TEST

The last gate, and the only one that catches what the others miss:

**Hand the compiled agent to someone with no access to you.** Not a
colleague who has heard you talk about it — someone cold. Can they use it
correctly without asking a question you would have to answer?

If they need you, the agent is not finished. It is a document about an agent
that lives in your head.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
VELCRO FOOTER

WHEN
  Version: 1.0 | Date: 2026-08-27

WHERE
  Repo: superbasic-agents/docs/CREATING-AN-AGENT-TYPE.md

WHICH
  Related Documents: SuperBasic™ Agent Standard (§3 anatomy, §3b roster,
    §5 the four tells) · Running an Agent · constitution-template.md
  Reference implementation: agents/researcher/constitution.md

VALID?
  Intention: Let someone build the eleventh archetype without the author
    present — the difference between shipping a tool and shipping a method.
  Research: None new. Sequence drawn from the Standard §3 and from the
    order the reference implementation was actually built in.
  Synthesis: §3's ordering (Iron Law first, Identity last) is the load-
    bearing claim and the one that most often gets inverted.
  Analysis: Full.
  Status: MET
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
